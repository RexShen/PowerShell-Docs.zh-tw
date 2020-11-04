---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: 6d060e0325ba10391f04348178f28b2793fe37fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203228"
---
# <span data-ttu-id="01701-103">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="01701-103">Import-Csv</span></span>

## <span data-ttu-id="01701-104">概要</span><span class="sxs-lookup"><span data-stu-id="01701-104">SYNOPSIS</span></span>
<span data-ttu-id="01701-105">以逗號分隔值 (CSV) 檔中的專案建立類似表格的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="01701-105">Creates table-like custom objects from the items in a comma-separated value (CSV) file.</span></span>

## <span data-ttu-id="01701-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01701-106">SYNTAX</span></span>

### <span data-ttu-id="01701-107">Delimiter (預設值)</span><span class="sxs-lookup"><span data-stu-id="01701-107">Delimiter (Default)</span></span>

```
Import-Csv [[-Path] <string[]>] [[-Delimiter] <char>] [-LiteralPath <string[]>] [-Header <string[]>]
 [-Encoding <string>] [<CommonParameters>]
```

### <span data-ttu-id="01701-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="01701-108">UseCulture</span></span>

```
Import-Csv [[-Path] <string[]>] -UseCulture [-LiteralPath <string[]>] [-Header <string[]>]
 [-Encoding <string>] [<CommonParameters>]
```

## <span data-ttu-id="01701-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01701-109">DESCRIPTION</span></span>

<span data-ttu-id="01701-110">`Import-Csv`Cmdlet 會從 CSV 檔案中的專案建立類似表格的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="01701-110">The `Import-Csv` cmdlet creates table-like custom objects from the items in CSV files.</span></span> <span data-ttu-id="01701-111">CSV 檔案中的每個資料行都會變成自訂物件的屬性，而資料列中的專案則會成為屬性值。</span><span class="sxs-lookup"><span data-stu-id="01701-111">Each column in the CSV file becomes a property of the custom object and the items in rows become the property values.</span></span> <span data-ttu-id="01701-112">`Import-Csv` 適用于任何 CSV 檔案，包括 Cmdlet 所產生的檔案 `Export-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-112">`Import-Csv` works on any CSV file, including files that are generated by the `Export-Csv` cmdlet.</span></span>

<span data-ttu-id="01701-113">您可以使用 Cmdlet 的參數 `Import-Csv` 來指定欄標題列和專案分隔符號，或直接 `Import-Csv` 使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="01701-113">You can use the parameters of the `Import-Csv` cmdlet to specify the column header row and the item delimiter, or direct `Import-Csv` to use the list separator for the current culture as the item delimiter.</span></span>

<span data-ttu-id="01701-114">您也可以使用 `ConvertTo-Csv` 和 `ConvertFrom-Csv` Cmdlet，將物件轉換為 CSV 字串 (和回) 。</span><span class="sxs-lookup"><span data-stu-id="01701-114">You can also use the `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets to convert objects to CSV strings (and back).</span></span> <span data-ttu-id="01701-115">這些 Cmdlet 與 `Export-CSV` 和 `Import-Csv` Cmdlet 相同，不同之處在于它們不會處理檔案。</span><span class="sxs-lookup"><span data-stu-id="01701-115">These cmdlets are the same as the `Export-CSV` and `Import-Csv` cmdlets, except that they do not deal with files.</span></span>

<span data-ttu-id="01701-116">如果 CSV 檔案中的標題列專案包含空白或 null 值，則 PowerShell 會插入預設標頭資料列名稱，並顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="01701-116">If a header row entry in a CSV file contains an empty or null value, PowerShell inserts a default header row name and displays a warning message.</span></span>

<span data-ttu-id="01701-117">`Import-Csv` 使用位元組順序標記 (BOM) 來偵測檔案的編碼格式。</span><span class="sxs-lookup"><span data-stu-id="01701-117">`Import-Csv` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="01701-118">如果檔案沒有 BOM，則會假設編碼為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="01701-118">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="01701-119">範例</span><span class="sxs-lookup"><span data-stu-id="01701-119">EXAMPLES</span></span>

### <span data-ttu-id="01701-120">範例1：匯入處理物件</span><span class="sxs-lookup"><span data-stu-id="01701-120">Example 1: Import process objects</span></span>

<span data-ttu-id="01701-121">這個範例示範如何匯出和匯入處理常式物件的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="01701-121">This example shows how to export and then import a CSV file of process objects.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

<span data-ttu-id="01701-122">`Get-Process`Cmdlet 會將處理常式物件向下傳送至 `Export-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-122">The `Get-Process` cmdlet sends process objects down the pipeline to the `Export-Csv`.</span></span> <span data-ttu-id="01701-123">`Export-Csv`Cmdlet 會將處理常式物件轉換為 CSV 字串，並將字串儲存在 Processes.csv 檔案中。</span><span class="sxs-lookup"><span data-stu-id="01701-123">The `Export-Csv` cmdlet converts the process objects to CSV strings and saves the strings in the Processes.csv file.</span></span> <span data-ttu-id="01701-124">`Import-Csv`Cmdlet 會從 Processes.csv 檔案匯入 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="01701-124">The `Import-Csv` cmdlet imports the CSV strings from the Processes.csv file.</span></span>
<span data-ttu-id="01701-125">字串會儲存在變數中 `$P` 。</span><span class="sxs-lookup"><span data-stu-id="01701-125">The strings are saved in the `$P` variable.</span></span> <span data-ttu-id="01701-126">`$P`變數會向下傳送至 `Get-Member` Cmdlet，以顯示已匯入之 CSV 字串的屬性。</span><span class="sxs-lookup"><span data-stu-id="01701-126">The `$P` variable is sent down the pipeline to the `Get-Member` cmdlet that displays the properties of the imported CSV strings.</span></span> <span data-ttu-id="01701-127">`$P`變數會向下傳送至 `Format-Table` Cmdlet，並顯示物件。</span><span class="sxs-lookup"><span data-stu-id="01701-127">The `$P` variable is sent down the pipeline to the `Format-Table` cmdlet and displays the objects.</span></span>

### <span data-ttu-id="01701-128">範例2：指定分隔符號</span><span class="sxs-lookup"><span data-stu-id="01701-128">Example 2: Specify the delimiter</span></span>

<span data-ttu-id="01701-129">此範例說明如何使用 Cmdlet 的 **分隔符號** 參數 `Import-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-129">This example shows how to use the **Delimiter** parameter of the `Import-Csv` cmdlet.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

<span data-ttu-id="01701-130">`Get-Process`Cmdlet 會將處理常式物件向下傳送至 `Export-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-130">The `Get-Process` cmdlet sends process objects down the pipeline to `Export-Csv`.</span></span> <span data-ttu-id="01701-131">`Export-Csv`Cmdlet 會將處理常式物件轉換為 CSV 字串，並將字串儲存在 Processes.csv 檔案中。</span><span class="sxs-lookup"><span data-stu-id="01701-131">The `Export-Csv` cmdlet converts the process objects to CSV strings and saves the strings in the Processes.csv file.</span></span>
<span data-ttu-id="01701-132">**分隔符號** 參數是用來指定冒號分隔符號。</span><span class="sxs-lookup"><span data-stu-id="01701-132">The **Delimiter** parameter is used to specify a colon delimiter.</span></span> <span data-ttu-id="01701-133">`Import-Csv`Cmdlet 會從 Processes.csv 檔案匯入 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="01701-133">The `Import-Csv` cmdlet imports the CSV strings from the Processes.csv file.</span></span> <span data-ttu-id="01701-134">字串會儲存在變數中 `$P` 。</span><span class="sxs-lookup"><span data-stu-id="01701-134">The strings are saved in the `$P` variable.</span></span> <span data-ttu-id="01701-135">To `$P` 變數會向下傳送至 `Format-Table` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01701-135">To `$P` variable is sent down the pipeline to the `Format-Table` cmdlet.</span></span>

### <span data-ttu-id="01701-136">範例3：指定分隔符號的目前文化特性</span><span class="sxs-lookup"><span data-stu-id="01701-136">Example 3: Specify the current culture for the delimiter</span></span>

<span data-ttu-id="01701-137">此範例說明如何搭配使用 `Import-Csv` Cmdlet 與 **UseCulture** 參數。</span><span class="sxs-lookup"><span data-stu-id="01701-137">This example shows how to use the `Import-Csv` cmdlet with the **UseCulture** parameter.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

<span data-ttu-id="01701-138">此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性來取得目前文化特性的預設清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="01701-138">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** to get the current culture's default list separator.</span></span> <span data-ttu-id="01701-139">`Get-Process`Cmdlet 會將處理常式物件向下傳送至 `Export-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-139">The `Get-Process` cmdlet sends process objects down the pipeline to `Export-Csv`.</span></span> <span data-ttu-id="01701-140">`Export-Csv`Cmdlet 會將處理常式物件轉換為 CSV 字串，並將字串儲存在 Processes.csv 檔案中。</span><span class="sxs-lookup"><span data-stu-id="01701-140">The `Export-Csv` cmdlet converts the process objects to CSV strings and saves the strings in the Processes.csv file.</span></span> <span data-ttu-id="01701-141">**UseCulture** 參數會使用目前文化特性的預設清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="01701-141">The **UseCulture** parameter uses the current culture's default list separator.</span></span> <span data-ttu-id="01701-142">`Import-Csv`Cmdlet 會從 Processes.csv 檔案匯入 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="01701-142">The `Import-Csv` cmdlet imports the CSV strings from the Processes.csv file.</span></span>

### <span data-ttu-id="01701-143">範例4：變更匯入物件中的屬性名稱</span><span class="sxs-lookup"><span data-stu-id="01701-143">Example 4: Change property names in an imported object</span></span>

<span data-ttu-id="01701-144">這個範例示範如何使用的 **Header** 參數 `Import-Csv` ，變更所產生匯入物件中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="01701-144">This example shows how to use the **Header** parameter of `Import-Csv` to change the names of properties in the resulting imported object.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished',
  'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error',
  'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

<span data-ttu-id="01701-145">`Start-Job`Cmdlet 會啟動執行的背景工作 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="01701-145">The `Start-Job` cmdlet starts a background job that runs `Get-Process`.</span></span> <span data-ttu-id="01701-146">工作物件會向下傳送至 `Export-Csv` Cmdlet，並轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="01701-146">A job object is sent down the pipeline to the `Export-Csv` cmdlet and converted to a CSV string.</span></span> <span data-ttu-id="01701-147">**NoTypeInformation** 參數會從 CSV 輸出移除類型資訊標頭，而且在 PowerShell Core 中是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="01701-147">The **NoTypeInformation** parameter removes the type information header from CSV output and is optional in PowerShell Core.</span></span>
<span data-ttu-id="01701-148">`$Header`變數包含會取代下列預設值的自訂標頭： **HasMoreData** 、 **JobStateInfo** 、 **PSBeginTime** 、 **PSEndTime** 和 **PSJobTypeName** 。</span><span class="sxs-lookup"><span data-stu-id="01701-148">The `$Header` variable contains a custom header that replaces the following default values: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** , and **PSJobTypeName** .</span></span> <span data-ttu-id="01701-149">此 `$A` 變數會使用 `Get-Content` Cmdlet 從 Jobs.csv 檔案取得 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="01701-149">The `$A` variable uses the `Get-Content` cmdlet to get the CSV string from the Jobs.csv file.</span></span> <span data-ttu-id="01701-150">`$A`變數是用來從檔案移除預設的標頭。</span><span class="sxs-lookup"><span data-stu-id="01701-150">The `$A` variable is used to remove the default header from the file.</span></span> <span data-ttu-id="01701-151">Cmdlet 會將 `Out-File` 新版本的 Jobs.csv 檔案儲存在變數中 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="01701-151">The `Out-File` cmdlet saves the new version of the Jobs.csv file in the `$A` variable.</span></span> <span data-ttu-id="01701-152">Cmdlet 會匯 `Import-Csv` 入 Jobs.csv 的檔案，並 **使用 Header** 參數來套用 `$Header` 變數。</span><span class="sxs-lookup"><span data-stu-id="01701-152">The `Import-Csv` cmdlet imports the Jobs.csv file and uses the **Header** parameter to apply the `$Header` variable.</span></span> <span data-ttu-id="01701-153">`$J`變數包含匯入的 **PSCustomObject** ，並在 PowerShell 主控台中顯示物件。</span><span class="sxs-lookup"><span data-stu-id="01701-153">The `$J` variable contains the imported **PSCustomObject** and displays the object in the PowerShell console.</span></span>

### <span data-ttu-id="01701-154">範例5：使用 CSV 檔案建立自訂物件</span><span class="sxs-lookup"><span data-stu-id="01701-154">Example 5: Create a custom object using a CSV file</span></span>

<span data-ttu-id="01701-155">此範例示範如何使用 CSV 檔案，在 PowerShell 中建立自訂物件。</span><span class="sxs-lookup"><span data-stu-id="01701-155">This example shows how to create a custom object in PowerShell by using a CSV file.</span></span>

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

<span data-ttu-id="01701-156">若要建立 Links.csv 檔案，請使用輸出中所顯示的值 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="01701-156">To create your Links.csv file, use the values shown in the `Get-Content` output.</span></span>

<span data-ttu-id="01701-157">`Get-Content`Cmdlet 會顯示 Links.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="01701-157">The `Get-Content` cmdlet displays the Links.csv file.</span></span> <span data-ttu-id="01701-158">Cmdlet 會匯 `Import-Csv` 入 Links.csv 的檔案。</span><span class="sxs-lookup"><span data-stu-id="01701-158">The `Import-Csv` cmdlet imports the Links.csv file.</span></span> <span data-ttu-id="01701-159">**Header** 參數會指定屬性名稱 **LinkId** 和 **TopicTitle** 。</span><span class="sxs-lookup"><span data-stu-id="01701-159">The **Header** parameter specifies the property names **LinkId** and **TopicTitle** .</span></span> <span data-ttu-id="01701-160">物件會儲存在變數中 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="01701-160">The objects are stored in the `$A` variable.</span></span> <span data-ttu-id="01701-161">此 `Get-Member` Cmdlet 會顯示 **標頭** 參數中的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="01701-161">The `Get-Member` cmdlet shows the property names from the **Header** parameter.</span></span> <span data-ttu-id="01701-162">此 `Where-Object` Cmdlet 會選取具有 **TopicTitle** 屬性（包含 **別名** ）的物件。</span><span class="sxs-lookup"><span data-stu-id="01701-162">The `Where-Object` cmdlet selects objects with the **TopicTitle** property that includes **alias** .</span></span>

### <span data-ttu-id="01701-163">範例6：匯入缺少值的 CSV</span><span class="sxs-lookup"><span data-stu-id="01701-163">Example 6: Import a CSV that is missing a value</span></span>

<span data-ttu-id="01701-164">此範例說明 `Import-Csv` 當 CSV 檔案中的標頭資料列包含 null 或空白值時，PowerShell 中的 Cmdlet 如何回應。</span><span class="sxs-lookup"><span data-stu-id="01701-164">This example shows how the `Import-Csv` cmdlet in PowerShell responds when the header row in a CSV file includes a null or empty value.</span></span> <span data-ttu-id="01701-165">`Import-Csv` 替代遺漏標頭資料列的預設名稱，該資料行會成為傳回之物件的屬性名稱 `Import-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-165">`Import-Csv` substitutes a default name for the missing header row that becomes the property name of the object that `Import-Csv` returns.</span></span>

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

<span data-ttu-id="01701-166">若要建立 Projects.csv 檔案，請使用範例輸出中所示的值 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="01701-166">To create your Projects.csv file, use the values shown in the example's `Get-Content` output.</span></span>

<span data-ttu-id="01701-167">`Get-Content`Cmdlet 會顯示 Projects.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="01701-167">The `Get-Content` cmdlet displays the Projects.csv file.</span></span> <span data-ttu-id="01701-168">標頭資料列缺少 **專案名稱** 與 **已完成** 之間的值。</span><span class="sxs-lookup"><span data-stu-id="01701-168">The header row is missing a value between **ProjectName** and **Completed** .</span></span> <span data-ttu-id="01701-169">`Import-Csv`Cmdlet 會匯入 Projects.csv 檔案並顯示警告訊息，因為 **H1** 是預設的標頭名稱。</span><span class="sxs-lookup"><span data-stu-id="01701-169">The `Import-Csv` cmdlet imports the Projects.csv file and displays a warning message because **H1** is a default header name.</span></span> <span data-ttu-id="01701-170">此 `(Import-Csv -Path
.\Projects.csv).H1` 命令會取得 **H1** 屬性值並顯示警告。</span><span class="sxs-lookup"><span data-stu-id="01701-170">The `(Import-Csv -Path
.\Projects.csv).H1` command gets the **H1** property values and displays a warning.</span></span>

## <span data-ttu-id="01701-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01701-171">PARAMETERS</span></span>

### <span data-ttu-id="01701-172">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="01701-172">-Delimiter</span></span>

<span data-ttu-id="01701-173">指定 CSV 檔案中用來分隔屬性值的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="01701-173">Specifies the delimiter that separates the property values in the CSV file.</span></span>
<span data-ttu-id="01701-174">預設值為逗號 (,)。</span><span class="sxs-lookup"><span data-stu-id="01701-174">The default is a comma (,).</span></span>

<span data-ttu-id="01701-175">輸入字元，例如冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="01701-175">Enter a character, such as a colon (:).</span></span>
<span data-ttu-id="01701-176">若要指定分號 (; ) 將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="01701-176">To specify a semicolon (;) enclose it in single quotation marks.</span></span>

<span data-ttu-id="01701-177">如果您在檔案中指定實際字串分隔符號以外的字元，就 `Import-Csv` 無法從 csv 字串建立物件，而且會傳回 csv 字串。</span><span class="sxs-lookup"><span data-stu-id="01701-177">If you specify a character other than the actual string delimiter in the file, `Import-Csv` cannot create the objects from the CSV strings and will return the CSV strings.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01701-178">-Encoding</span><span class="sxs-lookup"><span data-stu-id="01701-178">-Encoding</span></span>

<span data-ttu-id="01701-179">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="01701-179">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="01701-180">預設值是 `Default`。</span><span class="sxs-lookup"><span data-stu-id="01701-180">The default value is `Default`.</span></span>

<span data-ttu-id="01701-181">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="01701-181">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="01701-182">`ASCII` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="01701-182">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="01701-183">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="01701-183">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="01701-184">`Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="01701-184">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="01701-185">`OEM` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="01701-185">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="01701-186">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="01701-186">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="01701-187">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="01701-187">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="01701-188">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="01701-188">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="01701-189">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="01701-189">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01701-190">-Header</span><span class="sxs-lookup"><span data-stu-id="01701-190">-Header</span></span>

<span data-ttu-id="01701-191">指定匯入檔案的替代欄標題列。</span><span class="sxs-lookup"><span data-stu-id="01701-191">Specifies an alternate column header row for the imported file.</span></span> <span data-ttu-id="01701-192">欄標題會決定所建立物件的屬性名稱 `Import-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-192">The column header determines the property names of the objects created by `Import-Csv`.</span></span>

<span data-ttu-id="01701-193">以逗號分隔的清單形式輸入資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="01701-193">Enter column headers as a comma-separated list.</span></span> <span data-ttu-id="01701-194">不要使用引號括住標題字串。</span><span class="sxs-lookup"><span data-stu-id="01701-194">Do not enclose the header string in quotation marks.</span></span> <span data-ttu-id="01701-195">以單引號括住每個資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="01701-195">Enclose each column header in single quotation marks.</span></span>

<span data-ttu-id="01701-196">如果您輸入較少資料行的資料行標頭，則會捨棄其餘的資料行。</span><span class="sxs-lookup"><span data-stu-id="01701-196">If you enter fewer column headers than there are data columns, the remaining data columns are discarded.</span></span> <span data-ttu-id="01701-197">如果您輸入的資料行標題超過資料行的資料行，則會使用空的資料行來建立額外的資料行標題。</span><span class="sxs-lookup"><span data-stu-id="01701-197">If you enter more column headers than there are data columns, the additional column headers are created with empty data columns.</span></span>

<span data-ttu-id="01701-198">使用 **Header** 參數時，會從 CSV 檔案中刪除原始的標題列。</span><span class="sxs-lookup"><span data-stu-id="01701-198">When using the **Header** parameter, delete the original header row from the CSV file.</span></span> <span data-ttu-id="01701-199">否則，會 `Import-Csv` 從標頭資料列中的專案建立額外的物件。</span><span class="sxs-lookup"><span data-stu-id="01701-199">Otherwise, `Import-Csv` creates an extra object from the items in the header row.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01701-200">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="01701-200">-LiteralPath</span></span>

<span data-ttu-id="01701-201">指定要匯入的 CSV 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="01701-201">Specifies the path to the CSV file to import.</span></span> <span data-ttu-id="01701-202">與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="01701-202">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="01701-203">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="01701-203">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="01701-204">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="01701-204">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="01701-205">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="01701-205">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="01701-206">-Path</span><span class="sxs-lookup"><span data-stu-id="01701-206">-Path</span></span>

<span data-ttu-id="01701-207">指定要匯入的 CSV 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="01701-207">Specifies the path to the CSV file to import.</span></span>
<span data-ttu-id="01701-208">您也可以使用管線將路徑傳送至 `Import-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-208">You can also pipe a path to `Import-Csv`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="01701-209">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="01701-209">-UseCulture</span></span>

<span data-ttu-id="01701-210">使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="01701-210">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="01701-211">若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="01701-211">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01701-212">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01701-212">CommonParameters</span></span>

<span data-ttu-id="01701-213">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="01701-213">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01701-214">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="01701-214">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01701-215">輸入</span><span class="sxs-lookup"><span data-stu-id="01701-215">INPUTS</span></span>

### <span data-ttu-id="01701-216">System.String</span><span class="sxs-lookup"><span data-stu-id="01701-216">System.String</span></span>

<span data-ttu-id="01701-217">您可以使用管線將包含路徑的字串傳送至 `Import-Csv` 。</span><span class="sxs-lookup"><span data-stu-id="01701-217">You can pipe a string that contains a path to `Import-Csv`.</span></span>

## <span data-ttu-id="01701-218">輸出</span><span class="sxs-lookup"><span data-stu-id="01701-218">OUTPUTS</span></span>

### <span data-ttu-id="01701-219">Object</span><span class="sxs-lookup"><span data-stu-id="01701-219">Object</span></span>

<span data-ttu-id="01701-220">此 Cmdlet 會傳回 CSV 檔案中內容所描述的物件。</span><span class="sxs-lookup"><span data-stu-id="01701-220">This cmdlet returns the objects described by the content in the CSV file.</span></span>

## <span data-ttu-id="01701-221">注意</span><span class="sxs-lookup"><span data-stu-id="01701-221">NOTES</span></span>

<span data-ttu-id="01701-222">由於匯入的物件為 CSV 版本的物件類型，因此無法辨識這些物件，並以格式化物件類型非 CSV 版本的 PowerShell 類型格式化專案來格式化。</span><span class="sxs-lookup"><span data-stu-id="01701-222">Because the imported objects are CSV versions of the object type, they are not recognized and formatted by the PowerShell type formatting entries that format the non-CSV versions of the object type.</span></span>

<span data-ttu-id="01701-223">命令的結果 `Import-Csv` 是形成類似表格的自訂物件的字串集合。</span><span class="sxs-lookup"><span data-stu-id="01701-223">The result of an `Import-Csv` command is a collection of strings that form a table-like custom object.</span></span> <span data-ttu-id="01701-224">每個資料列都是不同的字串，因此您可以使用物件的 **count** 屬性來計算資料表資料列的計數。</span><span class="sxs-lookup"><span data-stu-id="01701-224">Each row is a separate string, so you can use the **Count** property of the object to count the table rows.</span></span> <span data-ttu-id="01701-225">欄是物件的屬性，而列中的項目是屬性值。</span><span class="sxs-lookup"><span data-stu-id="01701-225">The columns are the properties of the object and items in the rows are the property values.</span></span>

<span data-ttu-id="01701-226">欄標題列會決定欄數和欄名稱。</span><span class="sxs-lookup"><span data-stu-id="01701-226">The column header row determines the number of columns and the column names.</span></span> <span data-ttu-id="01701-227">欄名稱也是物件的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="01701-227">The column names are also the names of the properties of the objects.</span></span> <span data-ttu-id="01701-228">除非您使用 Header 參數來指定欄標題，否則第一個資料列會被轉譯為 **資料** 行標頭。</span><span class="sxs-lookup"><span data-stu-id="01701-228">The first row is interpreted to be the column headers, unless you use the **Header** parameter to specify column headers.</span></span> <span data-ttu-id="01701-229">如果有任何列包含的值比標題列還多，即會忽略額外的值。</span><span class="sxs-lookup"><span data-stu-id="01701-229">If any row has more values than the header row, the additional values are ignored.</span></span>

<span data-ttu-id="01701-230">如果資料行標頭資料列遺漏值，或包含 null 或空白值， `Import-Csv` 則會使用 **H** ，後面接著一個數位來表示遺漏的資料行標頭和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="01701-230">If the column header row is missing a value or contains a null or empty value, `Import-Csv` uses **H** followed by a number for the missing column header and property name.</span></span>

<span data-ttu-id="01701-231">在 CSV 檔案中，每個物件都會利用以逗號分隔的物件屬性值清單來表示。</span><span class="sxs-lookup"><span data-stu-id="01701-231">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="01701-232">屬性值會使用物件的 **ToString ( # B1** 方法轉換成字串，因此它們會以屬性值的名稱表示。</span><span class="sxs-lookup"><span data-stu-id="01701-232">The property values are converted to strings by using the **ToString()** method of the object, so they are represented by the name of the property value.</span></span> <span data-ttu-id="01701-233">`Export-Csv` 不會匯出物件的方法。</span><span class="sxs-lookup"><span data-stu-id="01701-233">`Export-Csv` does not export the methods of the object.</span></span>

## <span data-ttu-id="01701-234">相關連結</span><span class="sxs-lookup"><span data-stu-id="01701-234">RELATED LINKS</span></span>

[<span data-ttu-id="01701-235">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="01701-235">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="01701-236">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="01701-236">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="01701-237">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="01701-237">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="01701-238">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="01701-238">Get-Culture</span></span>](Get-Culture.md)