---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 5a76f8ec454ad8144f193d8927f913b89a429fec
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203307"
---
# <span data-ttu-id="bb384-103">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="bb384-103">Export-Csv</span></span>

## <span data-ttu-id="bb384-104">概要</span><span class="sxs-lookup"><span data-stu-id="bb384-104">SYNOPSIS</span></span>
<span data-ttu-id="bb384-105">將物件轉換成一系列的逗號分隔值 (CSV) 字串，並將字串儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-105">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="bb384-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb384-106">SYNTAX</span></span>

### <span data-ttu-id="bb384-107">Delimiter (預設值)</span><span class="sxs-lookup"><span data-stu-id="bb384-107">Delimiter (Default)</span></span>

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bb384-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="bb384-108">UseCulture</span></span>

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="bb384-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bb384-109">DESCRIPTION</span></span>

<span data-ttu-id="bb384-110">`Export-CSV`Cmdlet 會建立您所提交之物件的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-110">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="bb384-111">每個物件都是一個資料列，其中包含以逗號分隔的物件屬性值清單。</span><span class="sxs-lookup"><span data-stu-id="bb384-111">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="bb384-112">您可以使用 `Export-CSV` Cmdlet 來建立試算表，並與接受 CSV 檔案做為輸入的程式共用資料。</span><span class="sxs-lookup"><span data-stu-id="bb384-112">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="bb384-113">將物件傳送至 Cmdlet 之前，請勿先將物件格式化 `Export-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="bb384-113">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="bb384-114">如果 `Export-CSV` 接收格式化的物件，則 CSV 檔案會包含格式屬性，而不是物件屬性。</span><span class="sxs-lookup"><span data-stu-id="bb384-114">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="bb384-115">若只要匯出選取的物件屬性，請使用 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-115">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="bb384-116">範例</span><span class="sxs-lookup"><span data-stu-id="bb384-116">EXAMPLES</span></span>

### <span data-ttu-id="bb384-117">範例1：將進程屬性匯出至 CSV 檔案</span><span class="sxs-lookup"><span data-stu-id="bb384-117">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="bb384-118">此範例會選取具有特定屬性的 **處理** 程式物件，並將物件匯出至 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-118">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

<span data-ttu-id="bb384-119">`Get-Process`Cmdlet 會取得 **處理** 程式物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-119">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="bb384-120">**Name** 參數會篩選輸出，只包含 WmiPrvSE 處理物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-120">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="bb384-121">處理常式物件會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-121">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="bb384-122">`Select-Object` 使用 **Property** 參數來選取處理常式物件屬性的子集。</span><span class="sxs-lookup"><span data-stu-id="bb384-122">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="bb384-123">處理常式物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-123">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-124">`Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-124">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="bb384-125">**Path** 參數指定 WmiData.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-125">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-126">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-126">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-127">此 `Import-Csv` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-127">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="bb384-128">範例2：將進程匯出至逗號分隔的檔案</span><span class="sxs-lookup"><span data-stu-id="bb384-128">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="bb384-129">這個範例會取得 **處理** 程式物件，並將物件匯出至 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-129">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="bb384-130">`Get-Process`Cmdlet 會取得 **處理** 程式物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-130">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="bb384-131">處理常式物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-131">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-132">`Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-132">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="bb384-133">**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-133">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-134">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-134">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-135">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-135">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="bb384-136">範例3：將進程匯出至分號分隔的檔案</span><span class="sxs-lookup"><span data-stu-id="bb384-136">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="bb384-137">此範例會取得 **處理** 程式物件，並將物件匯出為具有分號分隔符號的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-137">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="bb384-138">`Get-Process`Cmdlet 會取得 **處理** 程式物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-138">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="bb384-139">處理常式物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-139">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-140">`Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-140">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="bb384-141">**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-141">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-142">**分隔符號** 參數會指定分號來分隔字串值。</span><span class="sxs-lookup"><span data-stu-id="bb384-142">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="bb384-143">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-143">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-144">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-144">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="bb384-145">範例4：使用目前文化特性的清單分隔符號來匯出進程</span><span class="sxs-lookup"><span data-stu-id="bb384-145">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="bb384-146">這個範例會取得 **處理** 程式物件，並將物件匯出到檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-146">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="bb384-147">分隔符號是目前文化特性的清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bb384-147">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="bb384-148">此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性，並顯示目前文化特性的預設清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bb384-148">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="bb384-149">`Get-Process`Cmdlet 會取得 **處理** 程式物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-149">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="bb384-150">處理常式物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-150">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-151">`Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-151">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="bb384-152">**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-152">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-153">**UseCulture** 參數會使用目前文化特性的預設清單分隔符號做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bb384-153">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="bb384-154">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-154">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-155">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-155">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="bb384-156">範例5：匯出具有類型資訊的處理常式</span><span class="sxs-lookup"><span data-stu-id="bb384-156">Example 5: Export processes with type information</span></span>

<span data-ttu-id="bb384-157">此範例說明如何在 CSV 檔案中包含 **#TYPE** 的標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="bb384-157">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="bb384-158">在 PowerShell 6.0 之前的版本中， **#TYPE** 標頭是預設值。</span><span class="sxs-lookup"><span data-stu-id="bb384-158">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="bb384-159">`Get-Process`Cmdlet 會取得 **處理** 程式物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-159">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="bb384-160">處理常式物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-160">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-161">`Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-161">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="bb384-162">**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-162">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-163">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-163">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="bb384-164">範例6：匯出和附加物件至 CSV 檔案</span><span class="sxs-lookup"><span data-stu-id="bb384-164">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="bb384-165">此範例說明如何將物件匯出至 CSV 檔案，並使用 **Append** 參數將物件加入至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-165">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

<span data-ttu-id="bb384-166">`Get-Service`Cmdlet 會取得服務物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-166">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="bb384-167">**DisplayName** 參數會傳回包含 Word 應用程式的服務。</span><span class="sxs-lookup"><span data-stu-id="bb384-167">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="bb384-168">服務物件會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-168">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="bb384-169">`Select-Object` 使用 **Property** 參數來指定 **DisplayName** 和 **Status** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bb384-169">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="bb384-170">`$AppService`變數會儲存物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-170">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="bb384-171">這些 `$AppService` 物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-171">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-172">`Export-Csv` 將服務物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-172">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="bb384-173">**Path** 參數指定 Services.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-173">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-174">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-174">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-175">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-175">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="bb384-176">`Get-Service`和 `Select-Object` Cmdlet 會針對包含 word 視窗的服務重複執行。</span><span class="sxs-lookup"><span data-stu-id="bb384-176">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="bb384-177">`$WinService`變數會儲存服務物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-177">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="bb384-178">指令 `Export-Csv` 程式會使用 **Append** 參數來指定將 `$WinService` 物件加入至現有的 Services.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-178">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="bb384-179">此 `Get-Content` Cmdlet 會重複顯示已更新的檔案，其中包含附加的資料。</span><span class="sxs-lookup"><span data-stu-id="bb384-179">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="bb384-180">範例7：管線中的 Format Cmdlet 會建立非預期的結果</span><span class="sxs-lookup"><span data-stu-id="bb384-180">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="bb384-181">此範例示範為什麼在管線內不使用 format Cmdlet 是很重要的。</span><span class="sxs-lookup"><span data-stu-id="bb384-181">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="bb384-182">收到未預期的輸出時，請針對管線語法進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="bb384-182">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

<span data-ttu-id="bb384-183">`Get-Date`Cmdlet 會取得 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-183">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="bb384-184">物件會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-184">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="bb384-185">`Select-Object` 使用 **Property** 參數來選取物件屬性的子集。</span><span class="sxs-lookup"><span data-stu-id="bb384-185">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="bb384-186">物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-186">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-187">`Export-Csv` 將物件轉換成 CSV 格式。</span><span class="sxs-lookup"><span data-stu-id="bb384-187">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="bb384-188">**Path** 參數指定 DateTime.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-188">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-189">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-189">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-190">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-190">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="bb384-191">在 `Format-Table` 管線中使用 Cmdlet 來選取屬性時，會收到未預期的結果。</span><span class="sxs-lookup"><span data-stu-id="bb384-191">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="bb384-192">`Format-Table` 將表格格式物件沿著管線向下傳送至 `Export-Csv` Cmdlet，而不是 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-192">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="bb384-193">`Export-Csv` 將表格格式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-193">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="bb384-194">此 `Get-Content` Cmdlet 會顯示包含表格格式物件的 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-194">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="bb384-195">範例8：使用 Force 參數來覆寫唯讀檔案</span><span class="sxs-lookup"><span data-stu-id="bb384-195">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="bb384-196">這個範例會建立一個空白的唯讀檔案，並使用 **Force** 參數來更新檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-196">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="bb384-197">此 `New-Item` Cmdlet 會使用 **Path** 和 **ItemType** 參數，在目前的目錄中建立 ReadOnly.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-197">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="bb384-198">此 `Set-ItemProperty` Cmdlet 會使用 **Name** 和 **Value** 參數將檔案的 **IsReadOnly** 屬性變更為 true。</span><span class="sxs-lookup"><span data-stu-id="bb384-198">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="bb384-199">`Get-Process`Cmdlet 會取得 **處理** 程式物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-199">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="bb384-200">處理常式物件會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-200">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-201">`Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-201">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="bb384-202">**Path** 參數指定 ReadOnly.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-202">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="bb384-203">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-203">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="bb384-204">輸出顯示未寫入檔案，因為拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="bb384-204">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="bb384-205">**Force** 參數會新增至 `Export-Csv` Cmdlet，以強制匯出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-205">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="bb384-206">此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-206">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="bb384-207">範例9：使用 Force 參數搭配 Append</span><span class="sxs-lookup"><span data-stu-id="bb384-207">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="bb384-208">這個範例示範如何使用 **Force** 與 **Append** 參數。</span><span class="sxs-lookup"><span data-stu-id="bb384-208">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="bb384-209">結合這些參數時，可以將不相符的物件屬性寫入 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-209">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

<span data-ttu-id="bb384-210">運算式會建立具有 **Name** 和 **Version** 屬性的 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="bb384-210">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="bb384-211">這些值會儲存在 `$Content` 變數中。</span><span class="sxs-lookup"><span data-stu-id="bb384-211">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="bb384-212">此 `$Content` 變數會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-212">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-213">`Export-Csv` 使用 **Path** 參數，並將 ParmFile.csv 檔案儲存在目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb384-213">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="bb384-214">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="bb384-214">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="bb384-215">另一個運算式會以 **Name** 和 **Edition** 屬性來建立 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="bb384-215">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="bb384-216">這些值會儲存在 `$AdditionalContent` 變數中。</span><span class="sxs-lookup"><span data-stu-id="bb384-216">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="bb384-217">此 `$AdditionalContent` 變數會向下傳送至 `Export-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb384-217">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="bb384-218">**Append** 參數是用來將資料新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-218">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="bb384-219">附加失敗，因為 **版本\*\*\*\*與版本之間** 的屬性名稱不相符。</span><span class="sxs-lookup"><span data-stu-id="bb384-219">The append fails because there is a property name mismatch between **Version** and **Edition** .</span></span>

<span data-ttu-id="bb384-220">`Export-Csv`Cmdlet **force** 參數是用來強制匯出寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-220">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="bb384-221">已捨棄 **版本** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bb384-221">The **Edition** property is discarded.</span></span> <span data-ttu-id="bb384-222">此 `Import-Csv` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-222">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="bb384-223">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bb384-223">PARAMETERS</span></span>

### <span data-ttu-id="bb384-224">-Append</span><span class="sxs-lookup"><span data-stu-id="bb384-224">-Append</span></span>

<span data-ttu-id="bb384-225">使用這個參數 `Export-CSV` 可將 CSV 輸出新增至指定檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="bb384-225">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="bb384-226">如果沒有這個參數， `Export-CSV` 則會取代檔案內容而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="bb384-226">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="bb384-227">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="bb384-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-228">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="bb384-228">-Delimiter</span></span>

<span data-ttu-id="bb384-229">指定分隔符號以區隔屬性值。</span><span class="sxs-lookup"><span data-stu-id="bb384-229">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="bb384-230">預設值是逗號 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="bb384-230">The default is a comma (`,`).</span></span> <span data-ttu-id="bb384-231">輸入字元，例如冒號 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="bb384-231">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="bb384-232">若要指定分號 (`;`) ，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="bb384-232">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="bb384-233">-Encoding</span><span class="sxs-lookup"><span data-stu-id="bb384-233">-Encoding</span></span>

<span data-ttu-id="bb384-234">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="bb384-234">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="bb384-235">預設值是 `ASCII`。</span><span class="sxs-lookup"><span data-stu-id="bb384-235">The default value is `ASCII`.</span></span>

<span data-ttu-id="bb384-236">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="bb384-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bb384-237">`ASCII` 使用 ASCII (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="bb384-237">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="bb384-238">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="bb384-238">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="bb384-239">`Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="bb384-239">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="bb384-240">`OEM` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="bb384-240">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="bb384-241">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="bb384-241">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="bb384-242">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="bb384-242">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="bb384-243">`UTF8` 使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="bb384-243">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="bb384-244">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="bb384-244">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-245">-Force</span><span class="sxs-lookup"><span data-stu-id="bb384-245">-Force</span></span>

<span data-ttu-id="bb384-246">此參數可讓您 `Export-Csv` 以 **唯讀** 屬性覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-246">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="bb384-247">結合 **Force** 和 **Append** 參數時，包含不相符之屬性的物件可以寫入 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-247">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="bb384-248">只有符合的屬性會寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-248">Only the properties that match are written to the file.</span></span> <span data-ttu-id="bb384-249">捨棄不相符的屬性。</span><span class="sxs-lookup"><span data-stu-id="bb384-249">The mismatched properties are discarded.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-250">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bb384-250">-InputObject</span></span>

<span data-ttu-id="bb384-251">指定要匯出為 CSV 字串的物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-251">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="bb384-252">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="bb384-252">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="bb384-253">您也可以透過管線將物件傳送至 `Export-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="bb384-253">You can also pipe objects to `Export-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-254">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bb384-254">-LiteralPath</span></span>

<span data-ttu-id="bb384-255">指定 CSV 輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="bb384-255">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="bb384-256">與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="bb384-256">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="bb384-257">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bb384-257">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="bb384-258">如果路徑包含 escape 字元，請使用單引號。</span><span class="sxs-lookup"><span data-stu-id="bb384-258">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="bb384-259">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="bb384-259">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-260">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="bb384-260">-NoClobber</span></span>

<span data-ttu-id="bb384-261">使用此參數，就 `Export-CSV` 不會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-261">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="bb384-262">根據預設，如果檔案存在指定的路徑中， `Export-CSV` 會覆寫檔案而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="bb384-262">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-263">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="bb384-263">-NoTypeInformation</span></span>

<span data-ttu-id="bb384-264">從輸出中移除 **#TYPE** 資訊標頭。</span><span class="sxs-lookup"><span data-stu-id="bb384-264">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="bb384-265">此參數會成為 PowerShell 6.0 中的預設值，並包含以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="bb384-265">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-266">-Path</span><span class="sxs-lookup"><span data-stu-id="bb384-266">-Path</span></span>

<span data-ttu-id="bb384-267">必要參數，指定要儲存 CSV 輸出檔的位置。</span><span class="sxs-lookup"><span data-stu-id="bb384-267">A required parameter that specifies the location to save the CSV output file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-268">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="bb384-268">-UseCulture</span></span>

<span data-ttu-id="bb384-269">使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bb384-269">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="bb384-270">若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="bb384-270">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-271">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb384-271">-Confirm</span></span>

<span data-ttu-id="bb384-272">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bb384-272">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb384-273">-WhatIf</span></span>

<span data-ttu-id="bb384-274">防止 Cmdlet 進行處理或變更。</span><span class="sxs-lookup"><span data-stu-id="bb384-274">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="bb384-275">輸出會顯示執行 Cmdlet 後會發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="bb384-275">The output shows what would happen if the cmdlet were run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb384-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb384-276">CommonParameters</span></span>

<span data-ttu-id="bb384-277">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bb384-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb384-278">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bb384-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb384-279">輸入</span><span class="sxs-lookup"><span data-stu-id="bb384-279">INPUTS</span></span>

### <span data-ttu-id="bb384-280">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="bb384-280">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="bb384-281">您可以使用管線將任何具有擴充類型系統 (ETS) adapter 的物件傳送至 `Export-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="bb384-281">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="bb384-282">輸出</span><span class="sxs-lookup"><span data-stu-id="bb384-282">OUTPUTS</span></span>

### <span data-ttu-id="bb384-283">System.String</span><span class="sxs-lookup"><span data-stu-id="bb384-283">System.String</span></span>

<span data-ttu-id="bb384-284">CSV 清單會傳送至 Path 參數中指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-284">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="bb384-285">注意</span><span class="sxs-lookup"><span data-stu-id="bb384-285">NOTES</span></span>

<span data-ttu-id="bb384-286">`Export-CSV`Cmdlet 會將您提交的物件轉換成一系列的 CSV 字串，並將它們儲存在指定的文字檔中。</span><span class="sxs-lookup"><span data-stu-id="bb384-286">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="bb384-287">您可以使用將 `Export-CSV` 物件儲存在 csv 檔案中，然後使用 `Import-Csv` CMDLET 從 csv 檔案建立物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-287">You can use `Export-CSV` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the CSV file.</span></span>

<span data-ttu-id="bb384-288">在 CSV 檔案中，每個物件都會利用以逗號分隔的物件屬性值清單來表示。</span><span class="sxs-lookup"><span data-stu-id="bb384-288">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="bb384-289">屬性值會使用 **ToString ( # B1** 方法轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-289">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="bb384-290">字串會以屬性值名稱表示。</span><span class="sxs-lookup"><span data-stu-id="bb384-290">The strings are represented by the property value name.</span></span> <span data-ttu-id="bb384-291">' Export-CSV 不會匯出物件的方法。</span><span class="sxs-lookup"><span data-stu-id="bb384-291">\`Export-CSV does not export the methods of the object.</span></span>

<span data-ttu-id="bb384-292">CSV 字串的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="bb384-292">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="bb384-293">依預設，第一個字串包含 **#TYPE** 資訊標頭，後面接著物件類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="bb384-293">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="bb384-294">例如， **#TYPE 的系統診斷** 。</span><span class="sxs-lookup"><span data-stu-id="bb384-294">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="bb384-295">如果使用 **NoTypeInformation** ，則第一個字串會包含資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="bb384-295">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="bb384-296">標頭包含第一個物件的屬性名稱，做為逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="bb384-296">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="bb384-297">其餘的字串包含每個物件之屬性值的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="bb384-297">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="bb384-298">當您將多個物件提交至時 `Export-CSV` ，會 `Export-CSV` 根據您所提交之第一個物件的屬性來組織檔案。</span><span class="sxs-lookup"><span data-stu-id="bb384-298">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="bb384-299">如果其餘的物件不具有指定之屬性的其中之一，該物件的屬性值會是 null，以兩個連續的逗號表示。</span><span class="sxs-lookup"><span data-stu-id="bb384-299">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="bb384-300">如果其餘的物件有其他屬性，那些屬性值將不會包含在檔案中。</span><span class="sxs-lookup"><span data-stu-id="bb384-300">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="bb384-301">您可以使用 `Import-Csv` Cmdlet，從檔案中的 CSV 字串重新建立物件。</span><span class="sxs-lookup"><span data-stu-id="bb384-301">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="bb384-302">產生的物件是 CSV 版本的原始物件，包含屬性值的字串表示，而且不含方法。</span><span class="sxs-lookup"><span data-stu-id="bb384-302">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="bb384-303">`ConvertTo-Csv`和 `ConvertFrom-Csv` Cmdlet 會將物件轉換成 csv 字串和 csv 字串。</span><span class="sxs-lookup"><span data-stu-id="bb384-303">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="bb384-304">`Export-CSV` 與相同 `ConvertTo-CSV` ，不同之處在于它會將 CSV 字串儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="bb384-304">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="bb384-305">相關連結</span><span class="sxs-lookup"><span data-stu-id="bb384-305">RELATED LINKS</span></span>

[<span data-ttu-id="bb384-306">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="bb384-306">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="bb384-307">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="bb384-307">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="bb384-308">Format-Table</span><span class="sxs-lookup"><span data-stu-id="bb384-308">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="bb384-309">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="bb384-309">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="bb384-310">Select-Object</span><span class="sxs-lookup"><span data-stu-id="bb384-310">Select-Object</span></span>](Select-Object.md)
