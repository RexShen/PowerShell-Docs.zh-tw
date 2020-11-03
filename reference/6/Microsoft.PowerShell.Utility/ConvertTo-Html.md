---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 92413bae22e7783cd8a444d08df002336da4d0a8
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206008"
---
# <span data-ttu-id="4e8d2-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="4e8d2-103">ConvertTo-Html</span></span>

## <span data-ttu-id="4e8d2-104">概要</span><span class="sxs-lookup"><span data-stu-id="4e8d2-104">SYNOPSIS</span></span>
<span data-ttu-id="4e8d2-105">將 .NET 物件轉換成可在網頁瀏覽器中顯示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="4e8d2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e8d2-106">SYNTAX</span></span>

### <span data-ttu-id="4e8d2-107">頁面 (預設) </span><span class="sxs-lookup"><span data-stu-id="4e8d2-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="4e8d2-108">片段</span><span class="sxs-lookup"><span data-stu-id="4e8d2-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4e8d2-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4e8d2-109">DESCRIPTION</span></span>

<span data-ttu-id="4e8d2-110">`ConvertTo-Html`Cmdlet 會將 .net 物件轉換成可在網頁瀏覽器中顯示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="4e8d2-111">您可以使用這個 Cmdlet 在網頁中顯示命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="4e8d2-112">您可以使用的參數來 `ConvertTo-Html` 選取物件屬性、指定表格或清單格式、指定 HTML 頁標題、在物件的前後新增文字，以及只傳回表格或清單片段，而不是 STRICT DTD 頁面。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="4e8d2-113">當您將多個物件提交至時 `ConvertTo-Html` ，PowerShell 會根據您所提交之第一個物件的屬性，建立 (或列出) 的資料表。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="4e8d2-114">如果剩餘的物件不具有其中一個指定的屬性，該物件的屬性值將會是空的儲存格。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="4e8d2-115">如果其餘的物件有其他屬性，那些屬性值將不會包含在檔案中。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="4e8d2-116">範例</span><span class="sxs-lookup"><span data-stu-id="4e8d2-116">EXAMPLES</span></span>

### <span data-ttu-id="4e8d2-117">範例1：建立網頁以顯示日期</span><span class="sxs-lookup"><span data-stu-id="4e8d2-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="4e8d2-118">此命令建立一個顯示目前日期之屬性的 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="4e8d2-119">它會使用 **InputObject** 參數將命令的結果提交 `Get-Date` 至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="4e8d2-120">範例2：建立可顯示 PowerShell 別名的網頁</span><span class="sxs-lookup"><span data-stu-id="4e8d2-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="4e8d2-121">此命令會建立 HTML 網頁，以列出目前主控台中的 PowerShell 別名。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="4e8d2-122">此命令會使用 `Get-Alias` Cmdlet 來取得別名。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="4e8d2-123">它使用管線運算子 (`|`) 將別名傳送至 `ConvertTo-Html` Cmdlet，此 Cmdlet 會建立 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="4e8d2-124">此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `aliases.htm` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="4e8d2-125">範例3：建立可顯示 PowerShell 事件的網頁</span><span class="sxs-lookup"><span data-stu-id="4e8d2-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="4e8d2-126">此命令會建立一個名為 `pslog.htm` 的 HTML 網頁，以顯示本機電腦上 Windows PowerShell 事件記錄檔中的事件。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="4e8d2-127">它會使用 `Get-EventLog` Cmdlet 取得 Windows PowerShell 記錄檔中的事件，然後使用管線運算子 () 將 `|` 事件傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="4e8d2-128">此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `pslog.htm` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="4e8d2-129">此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `pslog.htm` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="4e8d2-130">範例4：建立網頁以顯示進程</span><span class="sxs-lookup"><span data-stu-id="4e8d2-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="4e8d2-131">這些命令建立並開啟一個 HTML 網頁，當中列出本機電腦上處理程序的名稱、路徑及公司。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="4e8d2-132">第一個命令會使用 `Get-Process` Cmdlet 來取得代表電腦上執行之處理常式的物件。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="4e8d2-133">此命令會使用管線運算子 (`|`) 將處理常式物件傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="4e8d2-134">此命令會使用 **Property** 參數來選取要包含在資料表中之進程物件的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="4e8d2-135">命令使用 **title** 參數指定 HTML 網頁的標題。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="4e8d2-136">此命令也會使用 `Out-File` Cmdlet 將產生的 HTML 傳送至名為 Proc.htm 的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="4e8d2-137">第二個命令會使用 `Invoke-Item` Cmdlet `Proc.htm` 在預設瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="4e8d2-138">範例5：建立用來顯示服務物件的網頁</span><span class="sxs-lookup"><span data-stu-id="4e8d2-138">Example 5: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

<span data-ttu-id="4e8d2-139">此命令會建立 Cmdlet 所傳回之服務物件的 HTML 網頁 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="4e8d2-140">此命令會使用 **CssUri** 參數指定 HTML 網頁的級聯樣式表。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="4e8d2-141">**CssUri** 參數會將其他 `<link rel="stylesheet" type="text/css" href="test.css">` 標記新增至產生的 HTML。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="4e8d2-142">標記中的 HREF 屬性包含樣式表的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="4e8d2-143">範例6：建立網頁以顯示服務物件</span><span class="sxs-lookup"><span data-stu-id="4e8d2-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="4e8d2-144">此命令會建立 Cmdlet 所傳回之服務物件的 HTML 網頁 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="4e8d2-145">命令使用 **As** 參數指定清單格式。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="4e8d2-146">Cmdlet 會 `Out-File` 將產生的 HTML 傳送至檔案 `Services.htm` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="4e8d2-147">範例7：建立目前日期的 web 資料表</span><span class="sxs-lookup"><span data-stu-id="4e8d2-147">Example 7: Create a web table for the current date</span></span>

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

<span data-ttu-id="4e8d2-148">此命令會使用 `ConvertTo-Html` 來產生目前日期的 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="4e8d2-149">此命令會使用 `Get-Date` Cmdlet 來取得目前的日期。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="4e8d2-150">它使用管線運算子 (|) 將結果傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="4e8d2-151">此 `ConvertTo-Html` 命令包含 **片段** 參數，此參數會將輸出限制為 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="4e8d2-152">因此，會省略 HTML 網頁的其他元素，例如 `<HEAD>` 和 `<BODY>` 標記。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="4e8d2-153">範例8：建立可顯示 PowerShell 事件的網頁</span><span class="sxs-lookup"><span data-stu-id="4e8d2-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="4e8d2-154">此命令會使用 `Get-EventLog` Cmdlet 從 Windows PowerShell 事件記錄檔取得事件。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="4e8d2-155">它使用管線運算子 (`|`) 將事件傳送至 `ConvertTo-Html` Cmdlet，以將事件轉換成 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="4e8d2-156">此 `ConvertTo-Html` 命令會使用 **Property** 參數，只選取事件 **的 ID** 、 **Level** 及 **Task** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="4e8d2-157">範例9：建立可顯示指定服務的網頁</span><span class="sxs-lookup"><span data-stu-id="4e8d2-157">Example 9: Create a web page to display specified services</span></span>

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

<span data-ttu-id="4e8d2-158">此命令會建立並開啟一個網頁，顯示電腦上以開頭的服務。它使用的 **Title** 、 **Body** 、 **PreContent** 和 **PostContent** 參數 `ConvertTo-Html` 來自訂輸出。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="4e8d2-159">命令的第一個部分 `Get-Service` 會使用 Cmdlet 來取得電腦上以開頭的服務。此命令會使用管線運算子 (`|`) 將結果傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="4e8d2-160">此命令也會使用 `Out-File` Cmdlet 將輸出傳送至 Services.htm 的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="4e8d2-161">分號 (`;`) 結束第一個命令並啟動第二個命令，此命令會使用 `Invoke-Item` Cmdlet `Services.htm` 在預設瀏覽器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="4e8d2-162">範例10：設定 HTML 的中繼屬性和字元集</span><span class="sxs-lookup"><span data-stu-id="4e8d2-162">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="4e8d2-163">此命令會建立網頁的 HTML，其具有重新整理、撰寫和關鍵字的中繼標記。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-163">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="4e8d2-164">頁面的字元集設定為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="4e8d2-164">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="4e8d2-165">範例11：將 HTML 設定為 XHTML 轉換 DTD</span><span class="sxs-lookup"><span data-stu-id="4e8d2-165">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="4e8d2-166">此命令會將傳回的 HTML DOCTYPE 設定為 XHTML 轉換 DTD</span><span class="sxs-lookup"><span data-stu-id="4e8d2-166">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="4e8d2-167">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4e8d2-167">PARAMETERS</span></span>

### <span data-ttu-id="4e8d2-168">-As</span><span class="sxs-lookup"><span data-stu-id="4e8d2-168">-As</span></span>

<span data-ttu-id="4e8d2-169">決定要將物件的格式設定為表格或清單。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-169">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="4e8d2-170">有效的值為 **資料表** 和 **清單** 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-170">Valid values are **Table** and **List** .</span></span> <span data-ttu-id="4e8d2-171">預設值為 **Table** 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-171">The default value is **Table** .</span></span>

<span data-ttu-id="4e8d2-172">**資料表** 值會產生類似于 PowerShell 資料表格式的 HTML 資料表。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-172">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="4e8d2-173">標題列會顯示屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-173">The header row displays the property names.</span></span> <span data-ttu-id="4e8d2-174">每個表格列皆代表一個物件，並會顯示該物件每個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-174">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="4e8d2-175">**List** 值會為每個類似于 PowerShell 清單格式的物件產生兩個數據行的 HTML 資料表。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-175">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="4e8d2-176">第一個資料行顯示內容名稱。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-176">The first column displays the property name.</span></span> <span data-ttu-id="4e8d2-177">第二欄顯示內容值。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-177">The second column displays the property value.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-178">-Body</span><span class="sxs-lookup"><span data-stu-id="4e8d2-178">-Body</span></span>

<span data-ttu-id="4e8d2-179">指定要在開頭 `<BODY>` 標記之後新增的文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-179">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="4e8d2-180">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-180">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-181">-字元集</span><span class="sxs-lookup"><span data-stu-id="4e8d2-181">-Charset</span></span>

<span data-ttu-id="4e8d2-182">指定要加入至開頭標記的文字 `<charset>` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-182">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="4e8d2-183">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-183">By default, there is no text in that position.</span></span>

<span data-ttu-id="4e8d2-184">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-184">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-185">-CssUri</span><span class="sxs-lookup"><span data-stu-id="4e8d2-185">-CssUri</span></span>

<span data-ttu-id="4e8d2-186">指定套用到 HTML 檔案之階層式樣式表 (CSS) 的統一資源識別項 (URI)。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-186">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="4e8d2-187">URI 包含在輸出中的樣式表連結內。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-187">The URI is included in a style sheet link in the output.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-188">-Fragment</span><span class="sxs-lookup"><span data-stu-id="4e8d2-188">-Fragment</span></span>

<span data-ttu-id="4e8d2-189">只產生 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-189">Generates only an HTML table.</span></span> <span data-ttu-id="4e8d2-190">將會省略 HTML、HEAD、TITLE 及 BODY 標記。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-190">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-191">-Head</span><span class="sxs-lookup"><span data-stu-id="4e8d2-191">-Head</span></span>

<span data-ttu-id="4e8d2-192">指定 `<HEAD>` 標記的內容。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-192">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="4e8d2-193">預設為 `<title\>HTML TABLE</title>`。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-193">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="4e8d2-194">如果您使用 **Head** 參數，則會忽略 **Title** 參數。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-194">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-195">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4e8d2-195">-InputObject</span></span>

<span data-ttu-id="4e8d2-196">指定要以 HTML 呈現的物件。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-196">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="4e8d2-197">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-197">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="4e8d2-198">如果您使用此參數提交多個物件（例如電腦上的所有服務），則 `ConvertTo-Html` 會建立一個資料表，以顯示集合或物件陣列的屬性。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-198">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="4e8d2-199">若要建立個別物件的表格，請使用管線運算子將物件輸送至 `ConvertTo-Html` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-199">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="4e8d2-200">-中繼</span><span class="sxs-lookup"><span data-stu-id="4e8d2-200">-Meta</span></span>

<span data-ttu-id="4e8d2-201">指定要加入至開頭標記的文字 `<meta>` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-201">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="4e8d2-202">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-202">By default, there is no text in that position.</span></span>

<span data-ttu-id="4e8d2-203">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-204">-PostContent</span><span class="sxs-lookup"><span data-stu-id="4e8d2-204">-PostContent</span></span>

<span data-ttu-id="4e8d2-205">指定要在結尾 `</TABLE>` 標記之後新增的文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-205">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="4e8d2-206">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-206">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="4e8d2-207">-PreContent</span><span class="sxs-lookup"><span data-stu-id="4e8d2-207">-PreContent</span></span>

<span data-ttu-id="4e8d2-208">指定要在開頭 `<TABLE>` 標記之前新增的文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-208">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="4e8d2-209">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-209">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="4e8d2-210">-Property</span><span class="sxs-lookup"><span data-stu-id="4e8d2-210">-Property</span></span>

<span data-ttu-id="4e8d2-211">將物件的指定屬性包含在 HTML 中。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-211">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="4e8d2-212">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-212">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="4e8d2-213">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-213">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="4e8d2-214">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="4e8d2-214">Valid key-value pairs are:</span></span>

- <span data-ttu-id="4e8d2-215"> (或標籤的名稱) - `<string>` (新增至 PowerShell 6.x) </span><span class="sxs-lookup"><span data-stu-id="4e8d2-215">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="4e8d2-216">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="4e8d2-216">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="4e8d2-217">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="4e8d2-217">FormatString - `<string>`</span></span>
- <span data-ttu-id="4e8d2-218">寬度- `<int32>` -必須大於 `0`</span><span class="sxs-lookup"><span data-stu-id="4e8d2-218">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="4e8d2-219">對齊-值可以是 `Left` 、 `Center` 或 `Right`</span><span class="sxs-lookup"><span data-stu-id="4e8d2-219">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="4e8d2-220">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-220">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-221">-Title</span><span class="sxs-lookup"><span data-stu-id="4e8d2-221">-Title</span></span>

<span data-ttu-id="4e8d2-222">指定 HTML 檔案的標題，也就是出現在 `<TITLE>` 標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-222">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-223">-過渡</span><span class="sxs-lookup"><span data-stu-id="4e8d2-223">-Transitional</span></span>

<span data-ttu-id="4e8d2-224">將 **doctype** 變更為 **xhtml 轉換 Dtd** ，預設 **DOCTYPE** 為 **xhtml Strict dtd** 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-224">Changes the **DOCTYPE** to **XHTML Transitional DTD** , Default **DOCTYPE** is **XHTML Strict DTD** .</span></span>

<span data-ttu-id="4e8d2-225">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-225">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4e8d2-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e8d2-226">CommonParameters</span></span>

<span data-ttu-id="4e8d2-227">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e8d2-228">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e8d2-229">輸入</span><span class="sxs-lookup"><span data-stu-id="4e8d2-229">INPUTS</span></span>

### <span data-ttu-id="4e8d2-230">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="4e8d2-230">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="4e8d2-231">您可以透過管道將任何 .NET 物件傳送至 `ConvertTo-Html` 。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-231">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="4e8d2-232">輸出</span><span class="sxs-lookup"><span data-stu-id="4e8d2-232">OUTPUTS</span></span>

### <span data-ttu-id="4e8d2-233">System.string 或 System.Xml.Xml檔</span><span class="sxs-lookup"><span data-stu-id="4e8d2-233">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="4e8d2-234">`ConvertTo-Html` 傳回組成有效 HTML 的一連串字串。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-234">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="4e8d2-235">注意</span><span class="sxs-lookup"><span data-stu-id="4e8d2-235">NOTES</span></span>

<span data-ttu-id="4e8d2-236">若要使用此 Cmdlet，請使用管線將一或多個物件傳送至 Cmdlet，或使用 **InputObject** 參數來指定物件。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-236">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="4e8d2-237">當輸入是由多個物件組成時，這兩個方法的輸出會非常不一樣。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-237">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="4e8d2-238">當您使用管線將多個物件傳送至 Cmdlet 時，PowerShell 會一次將物件傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-238">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="4e8d2-239">因此， `ConvertTo-Html` 會建立顯示個別物件的資料表。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-239">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="4e8d2-240">例如，如果您使用管線將電腦上的處理常式傳送至 `ConvertTo-Html` ，則產生的表格會顯示所有的處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-240">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="4e8d2-241">當您使用 **InputObject** 參數提交多個物件時，會 `ConvertTo-Html` 以集合或陣列的形式接收這些物件。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-241">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="4e8d2-242">因此，它會建立顯示陣列及其屬性 (而非顯示陣列中的項目) 的表格。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-242">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="4e8d2-243">例如，如果您使用 **InputObject** 將電腦上的處理常式提交至 `ConvertTo-Html` ，則產生的資料表會顯示物件陣列和其屬性。</span><span class="sxs-lookup"><span data-stu-id="4e8d2-243">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="4e8d2-244">為了符合 XHTML 嚴格 DTD，會據以修改 DOCTYPE 標記：</span><span class="sxs-lookup"><span data-stu-id="4e8d2-244">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="4e8d2-245">相關連結</span><span class="sxs-lookup"><span data-stu-id="4e8d2-245">RELATED LINKS</span></span>

[<span data-ttu-id="4e8d2-246">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="4e8d2-246">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="4e8d2-247">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="4e8d2-247">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="4e8d2-248">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="4e8d2-248">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="4e8d2-249">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="4e8d2-249">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="4e8d2-250">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="4e8d2-250">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="4e8d2-251">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="4e8d2-251">Import-Clixml</span></span>](Import-Clixml.md)
