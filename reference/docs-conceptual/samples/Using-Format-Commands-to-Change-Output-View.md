---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用格式命令變更輸出檢視
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400943"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="7ac39-103">使用格式命令變更輸出檢視</span><span class="sxs-lookup"><span data-stu-id="7ac39-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="7ac39-104">Windows PowerShell 的一組 Cmdlet 可讓您控制針對特定物件所顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ac39-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="7ac39-105">所有 Cmdlet 名稱的開頭都是動詞 **Format**。</span><span class="sxs-lookup"><span data-stu-id="7ac39-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="7ac39-106">它們可讓您選取要顯示的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="7ac39-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="7ac39-107">**Format** Cmdlet 是 **Format-Wide**、**Format-List**、**Format-Table** 和 **Format-Custom**。</span><span class="sxs-lookup"><span data-stu-id="7ac39-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="7ac39-108">在本使用者手冊中，我們只會描述 **Format-Wide**、**Format-List** 和 **Format-Table** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7ac39-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="7ac39-109">每個 Format Cmdlet 都有預設屬性，可在未指定要顯示的特定屬性時使用。</span><span class="sxs-lookup"><span data-stu-id="7ac39-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="7ac39-110">每個 Cmdlet 也都會使用相同的參數名稱 (**Property**) 來指定您想要顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ac39-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="7ac39-111">因為 **Format-Wide** 只會顯示單一屬性，所以其 **Property** 參數只使用單一值，但 **Format-List** 和 **Format-Table** 的屬性參數將接受屬性名稱清單。</span><span class="sxs-lookup"><span data-stu-id="7ac39-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="7ac39-112">如果您搭配使用 **Get-Process -Name powershell** 命令與兩個執行中 Windows PowerShell 執行個體，則會收到與下面類似的輸出︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="7ac39-113">在本節的其餘部分，我們將探討如何使用 **Format** Cmdlet 來變更這個命令的輸出顯示方式。</span><span class="sxs-lookup"><span data-stu-id="7ac39-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="7ac39-114">針對 Single-Item 輸出使用 Format-Wide</span><span class="sxs-lookup"><span data-stu-id="7ac39-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="7ac39-115">**Format-Wide** Cmdlet 預設只會顯示物件的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="7ac39-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="7ac39-116">與每個物件相關聯的資訊會顯示在單一資料行中︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="7ac39-117">您也可以指定非預設屬性：</span><span class="sxs-lookup"><span data-stu-id="7ac39-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="7ac39-118">使用資料行控制 Format-Wide 顯示</span><span class="sxs-lookup"><span data-stu-id="7ac39-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="7ac39-119">使用 **Format-Wide** Cmdlet，一次只能顯示單一屬性。</span><span class="sxs-lookup"><span data-stu-id="7ac39-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="7ac39-120">這樣適用於顯示一行只顯示一個元素的簡單清單。</span><span class="sxs-lookup"><span data-stu-id="7ac39-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="7ac39-121">若要取得簡單清單，請將 **Column** 屬性的值設為 1，方法是輸入：</span><span class="sxs-lookup"><span data-stu-id="7ac39-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="7ac39-122">針對清單檢視使用 Format-List</span><span class="sxs-lookup"><span data-stu-id="7ac39-122">Using Format-List for a List View</span></span>

<span data-ttu-id="7ac39-123">**Format-List** Cmdlet 以清單形式顯示物件，並在個別行上標上和顯示每個屬性：</span><span class="sxs-lookup"><span data-stu-id="7ac39-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="7ac39-124">您可以指定您想要的任意數目的屬性︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="7ac39-125">搭配使用 Format-List 與萬用字元取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="7ac39-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="7ac39-126">**Format-List** Cmdlet 可讓您使用萬用字元作為其 **Property** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="7ac39-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="7ac39-127">這可讓您顯示詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7ac39-127">This lets you display detailed information.</span></span> <span data-ttu-id="7ac39-128">通常，物件所含的資訊會比您需要的資訊還要多，這是 Windows PowerShell 預設未顯示所有屬性值的原因。</span><span class="sxs-lookup"><span data-stu-id="7ac39-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="7ac39-129">若要顯示物件的所有屬性，請使用 **Format-List -Property \&#42;** 命令。</span><span class="sxs-lookup"><span data-stu-id="7ac39-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="7ac39-130">下列命令會針對單一處理程序產生 60 行以上的輸出︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="7ac39-131">雖然 **Format-List** 命令適用於顯示詳細資料，但是，如果您想要輸出概觀包括許多項目，則較簡單的表格式檢視通常更為有用。</span><span class="sxs-lookup"><span data-stu-id="7ac39-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="7ac39-132">針對表格式輸出使用 Format-Table</span><span class="sxs-lookup"><span data-stu-id="7ac39-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="7ac39-133">如果您使用未指定屬性名稱的 **Format-Table** Cmdlet 來格式化 **Get-Process** 命令的輸出，則收到的輸出會與未執行任何格式化所收到的輸出完全相同。</span><span class="sxs-lookup"><span data-stu-id="7ac39-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="7ac39-134">原因是處理程序通常會以表格式格式顯示，這與大部分的 Windows PowerShell 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="7ac39-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="7ac39-135">改善 Format-Table 輸出 (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="7ac39-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="7ac39-136">雖然表格式檢視適用於顯示許多類似資訊，但是可能難以解譯顯示是否太窄無法顯示資料。</span><span class="sxs-lookup"><span data-stu-id="7ac39-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="7ac39-137">例如，如果您嘗試顯示處理程序路徑、識別碼、名稱和公司，則會截斷處理程序路徑和公司資料行的輸出︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="7ac39-138">如果您在執行 **Format-Table** 命令時指定 **AutoSize** 參數，則 Windows PowerShell 會根據您要顯示的實際資料來計算資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="7ac39-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="7ac39-139">這讓 **Path** 資料行更容易閱讀，但是仍然會截斷公司資料行︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="7ac39-140">**Format-Table** Cmdlet 可能仍然會截斷資料，但是只會在畫面結尾才這麼做。</span><span class="sxs-lookup"><span data-stu-id="7ac39-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="7ac39-141">如果屬性不是最後一個顯示的屬性，則會提供其所需的大小來正確顯示其最長的資料元素。</span><span class="sxs-lookup"><span data-stu-id="7ac39-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="7ac39-142">如果您在 **Property** 值清單中交換 **Path** 和 **Company** 的位置，則可以看到顯示公司名稱，但截斷路徑：</span><span class="sxs-lookup"><span data-stu-id="7ac39-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="7ac39-143">**Format-Table** 命令假設屬性越接近屬性清單開頭，就越重要。</span><span class="sxs-lookup"><span data-stu-id="7ac39-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="7ac39-144">因此，它會嘗試完整顯示最接近開頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="7ac39-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="7ac39-145">如果 **Format-Table** 命令無法顯示所有屬性，則會從顯示中移除一些資料行，並提供警告。</span><span class="sxs-lookup"><span data-stu-id="7ac39-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="7ac39-146">如果您將 **Name** 設為清單中的最後一個屬性，則可以看到這項行為：</span><span class="sxs-lookup"><span data-stu-id="7ac39-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="7ac39-147">在上面的輸出中，會截斷識別碼資料行，以將其放入清單中，並堆疊資料行標題。</span><span class="sxs-lookup"><span data-stu-id="7ac39-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="7ac39-148">自動重新調整資料行大小，不一定會執行您要的作業。</span><span class="sxs-lookup"><span data-stu-id="7ac39-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="7ac39-149">在資料行中讓 Format-Table 換行 (Wrap)</span><span class="sxs-lookup"><span data-stu-id="7ac39-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="7ac39-150">您可以使用 **Wrap** 參數，強制冗長的 **Format-Table** 資料在其顯示資料行中換行。</span><span class="sxs-lookup"><span data-stu-id="7ac39-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="7ac39-151">因為未一併指定 **AutoSize** 時會使用預設設定，所以單獨使用 **Wrap** 參數不一定會執行您預期的作業：</span><span class="sxs-lookup"><span data-stu-id="7ac39-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="7ac39-152">單獨使用 **Wrap** 參數的優點是不會讓處理變的太慢。</span><span class="sxs-lookup"><span data-stu-id="7ac39-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="7ac39-153">如果您執行大型目錄系統的遞迴檔案清單，則使用 **AutoSize** 時，可能需要很長的時間，並會在顯示第一個輸出項目之前使用大量記憶體。</span><span class="sxs-lookup"><span data-stu-id="7ac39-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="7ac39-154">如果您不在意系統負載，則搭配使用 **AutoSize** 與 **Wrap** 參數的運作效果極佳。</span><span class="sxs-lookup"><span data-stu-id="7ac39-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="7ac39-155">初始資料行一律會獲分配在一行上顯示項目所需的寬度，就像指定沒有 **Wrap** 參數的 **AutoSize** 一樣。</span><span class="sxs-lookup"><span data-stu-id="7ac39-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="7ac39-156">唯一的差異在於，必要時會讓最後一個資料行換行︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="7ac39-157">如果您先指定最寬的資料行，則可能不會顯示部分資料行，因此最安全的方式是先指定最小的資料元素。</span><span class="sxs-lookup"><span data-stu-id="7ac39-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="7ac39-158">在下列範例中，我們先指定極寬的路徑元素，甚至進行換行，但仍然遺失最後的 **Name** 資料行︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="7ac39-159">組織資料表輸出 (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="7ac39-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="7ac39-160">表格式輸出控制項的另一個有用參數是 **GroupBy**。</span><span class="sxs-lookup"><span data-stu-id="7ac39-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="7ac39-161">較長的表格式清單尤其很難進行比較。</span><span class="sxs-lookup"><span data-stu-id="7ac39-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="7ac39-162">**GroupBy** 參數會根據屬性值將輸出群組在一起。</span><span class="sxs-lookup"><span data-stu-id="7ac39-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="7ac39-163">例如，我們可以依據公司將處理程序群組在一起，並省略屬性清單中的公司值，讓公司更容易進行檢查︰</span><span class="sxs-lookup"><span data-stu-id="7ac39-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```