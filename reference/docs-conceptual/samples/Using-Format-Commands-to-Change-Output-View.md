---
ms.date: 10/22/2019
keywords: powershell,cmdlet
title: 使用格式命令變更輸出檢視
ms.openlocfilehash: 9d9854362b5150a99bdd0c02518599840c1fd42d
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444424"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="02658-103">使用格式命令變更輸出檢視</span><span class="sxs-lookup"><span data-stu-id="02658-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="02658-104">PowerShell 的一組 Cmdlet 可讓您控制如何針對特定物件顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-104">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="02658-105">所有 Cmdlet 名稱的開頭都是動詞 `Format`。</span><span class="sxs-lookup"><span data-stu-id="02658-105">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="02658-106">它們可讓您選取要顯示哪些屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-106">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="02658-107">此文章說明 `Format-Wide`、`Format-List` 與 `Format-Table` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="02658-107">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="02658-108">PowerShell 中的每個物件類型都有預設屬性，可在您未指定要顯示哪些屬性時使用。</span><span class="sxs-lookup"><span data-stu-id="02658-108">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="02658-109">每個 Cmdlet 也都會使用相同的 **Property** 參數來指定您要顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-109">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="02658-110">因為 `Format-Wide` 只會顯示單一屬性，其 **Property** 參數只會使用單一值，但 `Format-List` 與 `Format-Table` 的 property 參數接受屬性名稱清單。</span><span class="sxs-lookup"><span data-stu-id="02658-110">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="02658-111">在此範例中，`Get-Process` Cmdlet 的預設輸出顯示我們有兩個 Internet Explorer 執行個體正在執行。</span><span class="sxs-lookup"><span data-stu-id="02658-111">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="02658-112">**程序**物件的預設格式會顯示如下所示的屬性：</span><span class="sxs-lookup"><span data-stu-id="02658-112">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="02658-113">針對 Single-Item 輸出使用 Format-Wide</span><span class="sxs-lookup"><span data-stu-id="02658-113">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="02658-114">`Format-Wide` Cmdlet 預設只會顯示物件的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-114">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="02658-115">與每個物件相關聯的資訊會顯示在單一資料行中︰</span><span class="sxs-lookup"><span data-stu-id="02658-115">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="02658-116">您也可以指定非預設屬性：</span><span class="sxs-lookup"><span data-stu-id="02658-116">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="02658-117">使用資料行控制 Format-Wide 顯示</span><span class="sxs-lookup"><span data-stu-id="02658-117">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="02658-118">使用 `Format-Wide` Cmdlet，一次只能顯示單一屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-118">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="02658-119">這有助於在多個資料行中顯示大型清單。</span><span class="sxs-lookup"><span data-stu-id="02658-119">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="02658-120">針對清單檢視使用 Format-List</span><span class="sxs-lookup"><span data-stu-id="02658-120">Using Format-List for a List View</span></span>

<span data-ttu-id="02658-121">`Format-List` Cmdlet 會以清單形式顯示物件，並在個別行上標記和顯示每個屬性：</span><span class="sxs-lookup"><span data-stu-id="02658-121">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="02658-122">您可以指定您想要的任意數目的屬性︰</span><span class="sxs-lookup"><span data-stu-id="02658-122">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="02658-123">搭配使用 Format-List 與萬用字元取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="02658-123">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="02658-124">`Format-List` Cmdlet 可讓您使用萬用字元作為其 **Property** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="02658-124">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="02658-125">這可讓您顯示詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="02658-125">This lets you display detailed information.</span></span> <span data-ttu-id="02658-126">通常，物件所含的資訊會比您需要的資訊還要多，這是 PowerShell 預設未顯示所有屬性值的原因。</span><span class="sxs-lookup"><span data-stu-id="02658-126">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="02658-127">若要顯示物件的所有屬性，請使用 **Format-List -Property \&#42;** 命令。</span><span class="sxs-lookup"><span data-stu-id="02658-127">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="02658-128">下列命令會針對單一處理程序產生 60 行以上的輸出︰</span><span class="sxs-lookup"><span data-stu-id="02658-128">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="02658-129">雖然 `Format-List` 命令在顯示詳細資料方面非常實用，但若要取得包括許多項目之輸出的概觀，則較簡單的表格式檢視通常更為實用。</span><span class="sxs-lookup"><span data-stu-id="02658-129">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="02658-130">針對表格式輸出使用 Format-Table</span><span class="sxs-lookup"><span data-stu-id="02658-130">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="02658-131">如果您使用未指定屬性名稱的 `Format-Table` Cmdlet 來設定 `Get-Process` 命令輸出格式，則收到的輸出會與未使用 `Format` Cmdlet 的情況相同。</span><span class="sxs-lookup"><span data-stu-id="02658-131">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="02658-132">根據預設，PowerShell 會以表格格式格式顯示**程序**物件。</span><span class="sxs-lookup"><span data-stu-id="02658-132">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="02658-133">改善 Format-Table 輸出 (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="02658-133">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="02658-134">雖然表格式檢視適用於顯示許多資訊，但是若顯示器太窄而無法容納資料，則可能難以解譯。</span><span class="sxs-lookup"><span data-stu-id="02658-134">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="02658-135">在上述範例中，輸出會被截斷。</span><span class="sxs-lookup"><span data-stu-id="02658-135">In the previous example, the output is truncated.</span></span> <span data-ttu-id="02658-136">如果您在執行 `Format-Table` 命令時指定 **AutoSize** 參數，PowerShell 會根據顯示的實際資料計算欄寬。</span><span class="sxs-lookup"><span data-stu-id="02658-136">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="02658-137">這可讓欄變成可讀取。</span><span class="sxs-lookup"><span data-stu-id="02658-137">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="02658-138">`Format-Table` Cmdlet 可能仍然會截斷資料，但是只會在畫面結尾截斷。</span><span class="sxs-lookup"><span data-stu-id="02658-138">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="02658-139">如果屬性不是最後一個顯示的屬性，則會提供其所需的大小來正確顯示其最長的資料元素。</span><span class="sxs-lookup"><span data-stu-id="02658-139">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="02658-140">`Format-Table` 命令會假設屬性是依重要性順序列出的。</span><span class="sxs-lookup"><span data-stu-id="02658-140">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="02658-141">因此，它會嘗試完整顯示最接近開頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-141">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="02658-142">如果 `Format-Table` 命令無法顯示所有屬性，它會從顯示中移除一些欄。</span><span class="sxs-lookup"><span data-stu-id="02658-142">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="02658-143">您可以在 **DependentServices** 屬性先前的範例中看到此行為。</span><span class="sxs-lookup"><span data-stu-id="02658-143">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="02658-144">在資料行中讓 Format-Table 換行 (Wrap)</span><span class="sxs-lookup"><span data-stu-id="02658-144">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="02658-145">您可以使用 **Wrap** 參數，強制冗長的 `Format-Table` 資料在其顯示欄中換行。</span><span class="sxs-lookup"><span data-stu-id="02658-145">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="02658-146">因為未一併指定 **AutoSize** 時會使用預設設定，所以單獨使用 **Wrap** 參數可能不會執行您預期的作業：</span><span class="sxs-lookup"><span data-stu-id="02658-146">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="02658-147">單獨使用 **Wrap** 參數不會讓處理速度變得太慢。</span><span class="sxs-lookup"><span data-stu-id="02658-147">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="02658-148">但是，使用 **AutoSize** 設定大型目錄結構的遞迴檔案清單格式時，可能需要很長的時間，並在顯示第一個輸出項目之前使用大量記憶體。</span><span class="sxs-lookup"><span data-stu-id="02658-148">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="02658-149">如果您不在意系統負載，搭配 **Wrap** 參數使用 **AutoSize** 並沒有問題。</span><span class="sxs-lookup"><span data-stu-id="02658-149">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="02658-150">初始欄仍會使用所需的寬度在一行上顯示項目，但如有必要，就會在最後一欄換行。</span><span class="sxs-lookup"><span data-stu-id="02658-150">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="02658-151">當您先指定最寬的欄時，某些欄就可能不會顯示。</span><span class="sxs-lookup"><span data-stu-id="02658-151">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="02658-152">為求最佳結果，請先指定最小的資料元素。</span><span class="sxs-lookup"><span data-stu-id="02658-152">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="02658-153">在下列範例中，我們會先指定最寬的屬性。</span><span class="sxs-lookup"><span data-stu-id="02658-153">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="02658-154">即使換行，也會省略最後的 **Id** 資料行：</span><span class="sxs-lookup"><span data-stu-id="02658-154">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="02658-155">組織資料表輸出 (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="02658-155">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="02658-156">表格式輸出控制項的另一個有用參數是 **GroupBy**。</span><span class="sxs-lookup"><span data-stu-id="02658-156">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="02658-157">較長的表格式清單尤其很難進行比較。</span><span class="sxs-lookup"><span data-stu-id="02658-157">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="02658-158">**GroupBy** 參數會根據屬性值將輸出群組在一起。</span><span class="sxs-lookup"><span data-stu-id="02658-158">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="02658-159">例如，我們可以依 **StartType** 將服務分組，並省略屬性清單中的 **StartType** 值，以方便檢查︰</span><span class="sxs-lookup"><span data-stu-id="02658-159">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
