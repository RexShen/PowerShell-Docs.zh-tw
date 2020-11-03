---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 4880e4adc9b4ebc339eb44a114e8e6d8bea398a6
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205899"
---
# <span data-ttu-id="bf1c7-103">Format-Table</span><span class="sxs-lookup"><span data-stu-id="bf1c7-103">Format-Table</span></span>

## <span data-ttu-id="bf1c7-104">概要</span><span class="sxs-lookup"><span data-stu-id="bf1c7-104">SYNOPSIS</span></span>
<span data-ttu-id="bf1c7-105">將輸出格式化為表格。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-105">Formats the output as a table.</span></span>

## <span data-ttu-id="bf1c7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf1c7-106">SYNTAX</span></span>

### <span data-ttu-id="bf1c7-107">全部</span><span class="sxs-lookup"><span data-stu-id="bf1c7-107">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="bf1c7-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bf1c7-108">DESCRIPTION</span></span>

<span data-ttu-id="bf1c7-109">Cmdlet 會將 `Format-Table` 命令的輸出格式化為表格，並在每個資料行中使用物件的已選取屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-109">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="bf1c7-110">物件類型會決定每個資料行中顯示的預設配置和屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-110">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="bf1c7-111">您可以使用 **Property** 參數來選取要顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-111">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="bf1c7-112">PowerShell 會使用預設格式器來定義如何顯示物件類型。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-112">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="bf1c7-113">您可以使用檔案 `.ps1xml` 來建立自訂視圖，以顯示具有指定屬性的輸出資料表。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-113">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="bf1c7-114">建立自訂視圖之後，請使用 **view** 參數以您的自訂視圖顯示資料表。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-114">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="bf1c7-115">如需有關 views 的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-115">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="bf1c7-116">您可以使用雜湊表，在顯示物件之前先將其加入至物件，並指定資料表中的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-116">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="bf1c7-117">若要加入計算屬性，請使用 **property** 或 **GroupBy** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-117">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="bf1c7-118">如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-118">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="bf1c7-119">範例</span><span class="sxs-lookup"><span data-stu-id="bf1c7-119">EXAMPLES</span></span>

### <span data-ttu-id="bf1c7-120">範例1：設定 PowerShell 主機的格式</span><span class="sxs-lookup"><span data-stu-id="bf1c7-120">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="bf1c7-121">此範例會顯示資料表中 PowerShell 之主機程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-121">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="bf1c7-122">指令 `Get-Host` 程式會 **InternalHost** 代表主機的........... 物件。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-122">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="bf1c7-123">物件會沿著管線向下傳送 `Format-Table` ，並顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-123">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="bf1c7-124">**AutoSize** 參數會調整資料行寬度，以將截斷降至最低。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-124">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="bf1c7-125">範例2：依根據 basepriority 格式化進程</span><span class="sxs-lookup"><span data-stu-id="bf1c7-125">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="bf1c7-126">在此範例中，處理常式會顯示在具有相同 **根據 basepriority** 屬性的群組中。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-126">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="bf1c7-127">指令 `Get-Process` 程式會取得代表電腦上每個處理常式的物件，並將其傳送到管線 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-127">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="bf1c7-128">物件會依照其 **根據 basepriority** 屬性的順序排序。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-128">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="bf1c7-129">排序的物件會向下傳送到管線 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-129">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="bf1c7-130">**GroupBy** 參數會根據其 **根據 basepriority** 屬性的值，將處理常式資料排列成群組。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-130">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="bf1c7-131">**Wrap** 參數可確保資料不會被截斷。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-131">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="bf1c7-132">範例3：依開始日期格式化進程</span><span class="sxs-lookup"><span data-stu-id="bf1c7-132">Example 3: Format processes by start date</span></span>

<span data-ttu-id="bf1c7-133">此範例會顯示電腦上執行之處理常式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-133">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="bf1c7-134">物件會進行排序，並 `Format-Table` 使用視圖依其開始日期將物件分組。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-134">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="bf1c7-135">`Get-Process` 取得代表電腦上執行之處理 **程式的處理常式** 物件。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-135">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="bf1c7-136">物件會沿著管線向下傳送至 `Sort-Object` ，並根據 **StartTime** 屬性來排序。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-136">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="bf1c7-137">排序的物件會向下傳送到管線 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-137">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="bf1c7-138">**View** 參數會指定在 PowerShell 檔案中針對 system.string 物件定義的 **StartTime** View。 `DotNetTypes.format.ps1xml` **System.Diagnostics.Process**</span><span class="sxs-lookup"><span data-stu-id="bf1c7-138">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="bf1c7-139">**StartTime** view 會將每個處理常式的開始時間轉換為簡短日期，然後依開始日期將處理常式分組。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-139">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="bf1c7-140">檔案 `DotNetTypes.format.ps1xml` 包含處理常式的 **優先權** 視圖。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-140">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="bf1c7-141">您可以 `format.ps1xml` 使用自訂的視圖來建立自己的檔案。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-141">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="bf1c7-142">範例4：針對資料表輸出使用自訂視圖</span><span class="sxs-lookup"><span data-stu-id="bf1c7-142">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="bf1c7-143">在此範例中，自訂視圖會顯示目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-143">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="bf1c7-144">自訂視圖會將 **CreationTime** 資料行加入到所建立之 **DirectoryInfo** 和 **FileInfo** 物件的資料表輸出中 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-144">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="bf1c7-145">此範例中的自訂視圖是從 PowerShell 原始程式碼中定義的視圖所建立。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-145">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="bf1c7-146">如需有關用來建立此範例視圖的視圖和程式碼的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-146">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

<span data-ttu-id="bf1c7-147">`Get-ChildItem` 取得目前目錄的內容 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-147">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="bf1c7-148">**DirectoryInfo** 和 **FileInfo** 物件會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-148">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="bf1c7-149">`Format-Table`使用 **View** 參數來指定包含 **CreationTime** 資料行的自訂視圖 **mygciview** 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-149">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="bf1c7-150">的預設 `Format-Table` 輸出 `Get-ChildItem` 不包含 **CreationTime** 資料行。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-150">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="bf1c7-151">範例5：使用資料表輸出的屬性</span><span class="sxs-lookup"><span data-stu-id="bf1c7-151">Example 5: Use properties for table output</span></span>

<span data-ttu-id="bf1c7-152">這個範例會使用 **Property** 參數，在顯示內容 **名稱** 和 **DependentServices** 的兩個數據行資料表中顯示所有電腦的服務。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-152">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices** .</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="bf1c7-153">`Get-Service` 取得電腦上的所有服務，並將 **system.serviceprocess.dll 的 ServiceController** 物件向下傳送到管線。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-153">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="bf1c7-154">`Format-Table` 使用 **Property** 參數來指定 **名稱** 和 **DependentServices** 屬性會顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-154">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="bf1c7-155">**Name** 和 **DependentServices** 是物件類型的兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-155">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="bf1c7-156">若要查看所有屬性： `Get-Service | Get-Member -MemberType Properties` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-156">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="bf1c7-157">範例6：設定進程的格式並計算其執行時間</span><span class="sxs-lookup"><span data-stu-id="bf1c7-157">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="bf1c7-158">這個範例會顯示一個資料表，其中包含本機電腦的「 **記事本** 」處理常式的處理常式名稱和總執行時間。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-158">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="bf1c7-159">總執行時間是從目前時間減去每個處理程序開始時間計算得來的。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-159">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

<span data-ttu-id="bf1c7-160">`Get-Process` 取得所有本機電腦的「 **記事本** 」處理常式，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-160">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="bf1c7-161">`Format-Table` 顯示具有兩個數據行的資料表： **ProcessName** 、 `Get-Process` 屬性和 **TotalRunningTime** （計算屬性）。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-161">`Format-Table` displays a table with two columns: **ProcessName** , a `Get-Process` property, and **TotalRunningTime** , a calculated property.</span></span>

<span data-ttu-id="bf1c7-162">**TotalRunningTime** 屬性是由含有兩個索引鍵、 **標籤** 和 **運算式** 的雜湊表所指定。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-162">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression** .</span></span> <span data-ttu-id="bf1c7-163">**標籤** 索引鍵會指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-163">The **Label** key specifies the property name.</span></span> <span data-ttu-id="bf1c7-164">**Expression** 索引鍵會指定計算。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-164">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="bf1c7-165">運算式會取得每個處理常式物件的 **StartTime** 屬性，並從命令的結果減去它 `Get-Date` ，以取得目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-165">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="bf1c7-166">範例7：設定記事本進程的格式</span><span class="sxs-lookup"><span data-stu-id="bf1c7-166">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="bf1c7-167">這個範例會使用 `Get-CimInstance` 來取得本機電腦上所有 **記事本** 處理常式的執行時間。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-167">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="bf1c7-168">您可以使用 `Get-CimInstance` With **ComputerName** 參數來取得遠端電腦的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-168">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

<span data-ttu-id="bf1c7-169">`Get-CimInstance` 取得 WMI **Win32_Process** 類別的實例，該類別會描述所有名為 **notepad.exe** 的本機電腦進程。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-169">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe** .</span></span> <span data-ttu-id="bf1c7-170">處理常式物件會儲存在 `$Processes` 變數中。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-170">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="bf1c7-171">變數中的處理常式物件 `$Processes` 會向下傳送到管線中 `Format-Table` ，這會顯示 **ProcessName** 屬性和新的計算屬性，即 **總執行時間** 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-171">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time** .</span></span>

<span data-ttu-id="bf1c7-172">此命令會將新的計算屬性名稱（ **總執行時間** ）指派給 **Label** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-172">The command assigns the name of the new calculated property, **Total Running Time** , to the **Label** key.</span></span> <span data-ttu-id="bf1c7-173">**運算式** 索引鍵的腳本區塊會計算目前日期的處理常式建立日期，以計算程式執行的時間長度。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-173">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="bf1c7-174">`Get-Date`Cmdlet 會取得目前的日期。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-174">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="bf1c7-175">建立日期會從目前日期減去。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-175">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="bf1c7-176">結果是 **總執行時間** 的值。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-176">The result is the value of **Total Running Time** .</span></span>

### <span data-ttu-id="bf1c7-177">範例8：針對格式錯誤進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="bf1c7-177">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="bf1c7-178">下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-178">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday
Failed to evaluate expression " $_ / $null ".
    + CategoryInfo          : InvalidArgument: (11/27/2019 12:53:41:PSObject) [], RuntimeException
    + FullyQualifiedErrorId : mshExpressionError
```

## <span data-ttu-id="bf1c7-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf1c7-179">PARAMETERS</span></span>

### <span data-ttu-id="bf1c7-180">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="bf1c7-180">-AutoSize</span></span>

<span data-ttu-id="bf1c7-181">指出此 Cmdlet 會根據資料的寬度調整資料行大小和資料行數目。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-181">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="bf1c7-182">根據預設，欄大小和欄數是由檢視決定。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-182">By default, the column size and number are determined by the view.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-183">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="bf1c7-183">-DisplayError</span></span>

<span data-ttu-id="bf1c7-184">指出此 Cmdlet 會在命令列上顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-184">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="bf1c7-185">當您要將命令中的運算式格式化 `Format-Table` ，而且需要針對運算式進行疑難排解時，這個參數可以用來做為調試輔助。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-185">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-186">-Expand</span><span class="sxs-lookup"><span data-stu-id="bf1c7-186">-Expand</span></span>

<span data-ttu-id="bf1c7-187">指定集合物件的格式以及集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-187">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="bf1c7-188">這個參數是設計來將支援 [ICollection](/dotnet/api/system.collections.icollection) ([system.object](/dotnet/api/system.collections) 的物件格式化) 介面。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-188">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="bf1c7-189">預設值為 **EnumOnly** 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-189">The default value is **EnumOnly** .</span></span>
<span data-ttu-id="bf1c7-190">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="bf1c7-190">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bf1c7-191">**EnumOnly** ：顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-191">**EnumOnly** : Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="bf1c7-192">**CoreOnly** ：顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-192">**CoreOnly** : Displays the properties of the collection object.</span></span>
- <span data-ttu-id="bf1c7-193">**Both** ：顯示集合物件的屬性，以及集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-193">**Both** : Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-194">-Force</span><span class="sxs-lookup"><span data-stu-id="bf1c7-194">-Force</span></span>

<span data-ttu-id="bf1c7-195">指出此 Cmdlet 會指示 Cmdlet 顯示所有錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-195">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="bf1c7-196">搭配 **DisplayError** 或 **ShowError** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-196">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="bf1c7-197">根據預設，將錯誤物件寫入錯誤或顯示串流時，只會顯示某些錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-197">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-198">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="bf1c7-198">-GroupBy</span></span>

<span data-ttu-id="bf1c7-199">根據屬性值，在個別的資料表中指定排序的輸出。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-199">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="bf1c7-200">例如，您可以使用 **GroupBy** ，根據其狀態在不同的資料表中列出服務。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-200">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="bf1c7-201">輸入運算式或屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-201">Enter an expression or a property.</span></span> <span data-ttu-id="bf1c7-202">**GroupBy** 參數需要排序物件。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-202">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="bf1c7-203">使用 `Sort-Object` Cmdlet `Format-Table` 來將物件分組。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-203">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="bf1c7-204">**GroupBy** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-204">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="bf1c7-205">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-205">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="bf1c7-206">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="bf1c7-206">Valid key-value pairs are:</span></span>

- <span data-ttu-id="bf1c7-207">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="bf1c7-208">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-208">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="bf1c7-209">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-209">FormatString - `<string>`</span></span>

<span data-ttu-id="bf1c7-210">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-211">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="bf1c7-211">-HideTableHeaders</span></span>

<span data-ttu-id="bf1c7-212">省略表格中的欄標題。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-212">Omits the column headings from the table.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-213">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bf1c7-213">-InputObject</span></span>

<span data-ttu-id="bf1c7-214">指定要格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-214">Specifies the objects to format.</span></span> <span data-ttu-id="bf1c7-215">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-215">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="bf1c7-216">-Property</span><span class="sxs-lookup"><span data-stu-id="bf1c7-216">-Property</span></span>

<span data-ttu-id="bf1c7-217">指定顯示中出現的物件屬性及其出現順序。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-217">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="bf1c7-218">輸入一或多個屬性名稱（以逗號分隔），或使用雜湊表顯示計算屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-218">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="bf1c7-219">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-219">Wildcards are permitted.</span></span>

<span data-ttu-id="bf1c7-220">如果您省略這個參數，顯示在顯示中的屬性將取決於第一個物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-220">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="bf1c7-221">例如，如果第一個物件具有 **PropertyA** 和 **PropertyB** ，但後續的物件具有 **PropertyA** 、 **PropertyB** 和 **PropertyC** ，則只會顯示 **PropertyA** 和 **PropertyB** 標頭。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-221">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA** , **PropertyB** , and **PropertyC** , then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="bf1c7-222">**Property** 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-222">The **Property** parameter is optional.</span></span> <span data-ttu-id="bf1c7-223">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-223">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="bf1c7-224">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-224">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="bf1c7-225">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-225">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="bf1c7-226">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="bf1c7-226">Valid key-value pairs are:</span></span>

- <span data-ttu-id="bf1c7-227">名稱 (或標籤) `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-227">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="bf1c7-228">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-228">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="bf1c7-229">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-229">FormatString - `<string>`</span></span>
- <span data-ttu-id="bf1c7-230">寬度- `<int32>` -必須大於 `0`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-230">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="bf1c7-231">對齊-值可以是 `Left` 、 `Center` 或 `Right`</span><span class="sxs-lookup"><span data-stu-id="bf1c7-231">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="bf1c7-232">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-232">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bf1c7-233">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="bf1c7-233">-RepeatHeader</span></span>

<span data-ttu-id="bf1c7-234">在每個畫面填滿之後重複顯示資料表的標頭。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-234">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="bf1c7-235">當輸出輸送至分頁（例如 `less` 或） `more` 或使用螢幕讀取器進行分頁時，重複的標頭會很有用。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-235">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-236">-ShowError</span><span class="sxs-lookup"><span data-stu-id="bf1c7-236">-ShowError</span></span>

<span data-ttu-id="bf1c7-237">此參數會透過管線傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-237">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="bf1c7-238">當您要將命令中的運算式格式化 `Format-Table` ，而且需要針對運算式進行疑難排解時，這個參數可以用來做為調試輔助。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-238">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-239">-View</span><span class="sxs-lookup"><span data-stu-id="bf1c7-239">-View</span></span>

<span data-ttu-id="bf1c7-240">在 PowerShell 5.1 及更早版本中，預設的視圖會定義在中儲存的檔案中 `*.format.ps1xml` `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-240">In PowerShell 5.1 and earlier versions, the default views are defined in `*.format.ps1xml` files stored in `$PSHOME`.</span></span>

<span data-ttu-id="bf1c7-241">**View** 參數可讓您為數據表指定替代的格式或自訂的視圖。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-241">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="bf1c7-242">您可以使用預設的 PowerShell views 或建立自訂的視圖。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-242">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="bf1c7-243">如需如何建立自訂視圖的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-243">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="bf1c7-244">**View** 參數的替代和自訂視圖必須使用資料表格式，否則 `Format-Table` 會失敗。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-244">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="bf1c7-245">如果替代視圖是清單，請使用 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-245">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="bf1c7-246">如果替代視圖不是清單或資料表，請使用 `Format-Custom` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-246">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="bf1c7-247">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-247">You can't use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-248">-Wrap</span><span class="sxs-lookup"><span data-stu-id="bf1c7-248">-Wrap</span></span>

<span data-ttu-id="bf1c7-249">將超過欄寬度的文字顯示於下一行。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-249">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="bf1c7-250">根據預設，系統會截斷超過欄寬度的文字。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-250">By default, text that exceeds the column width is truncated.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf1c7-251">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf1c7-251">CommonParameters</span></span>

<span data-ttu-id="bf1c7-252">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-252">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf1c7-253">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-253">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf1c7-254">輸入</span><span class="sxs-lookup"><span data-stu-id="bf1c7-254">INPUTS</span></span>

### <span data-ttu-id="bf1c7-255">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="bf1c7-255">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="bf1c7-256">您可以將任何物件沿著管線向下傳送至 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-256">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="bf1c7-257">輸出</span><span class="sxs-lookup"><span data-stu-id="bf1c7-257">OUTPUTS</span></span>

### <span data-ttu-id="bf1c7-258">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="bf1c7-258">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="bf1c7-259">`Format-Table` 傳回代表資料表的格式物件。</span><span class="sxs-lookup"><span data-stu-id="bf1c7-259">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="bf1c7-260">注意</span><span class="sxs-lookup"><span data-stu-id="bf1c7-260">NOTES</span></span>

## <span data-ttu-id="bf1c7-261">相關連結</span><span class="sxs-lookup"><span data-stu-id="bf1c7-261">RELATED LINKS</span></span>

[<span data-ttu-id="bf1c7-262">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="bf1c7-262">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="bf1c7-263">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="bf1c7-263">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="bf1c7-264">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="bf1c7-264">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="bf1c7-265">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="bf1c7-265">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="bf1c7-266">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="bf1c7-266">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="bf1c7-267">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="bf1c7-267">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="bf1c7-268">Format-List</span><span class="sxs-lookup"><span data-stu-id="bf1c7-268">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="bf1c7-269">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="bf1c7-269">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="bf1c7-270">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="bf1c7-270">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="bf1c7-271">Get-Member</span><span class="sxs-lookup"><span data-stu-id="bf1c7-271">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="bf1c7-272">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bf1c7-272">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="bf1c7-273">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="bf1c7-273">Update-FormatData</span></span>](Update-FormatData.md)
