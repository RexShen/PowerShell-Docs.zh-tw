---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 618308bb03f47659b8fa932ac0bb029972546755
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205896"
---
# <span data-ttu-id="79859-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="79859-103">ConvertTo-Html</span></span>

## <span data-ttu-id="79859-104">概要</span><span class="sxs-lookup"><span data-stu-id="79859-104">SYNOPSIS</span></span>
<span data-ttu-id="79859-105">將 .NET 物件轉換成可在網頁瀏覽器中顯示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="79859-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="79859-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79859-106">SYNTAX</span></span>

### <span data-ttu-id="79859-107">頁面 (預設) </span><span class="sxs-lookup"><span data-stu-id="79859-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="79859-108">片段</span><span class="sxs-lookup"><span data-stu-id="79859-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="79859-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="79859-109">DESCRIPTION</span></span>

<span data-ttu-id="79859-110">`ConvertTo-Html`Cmdlet 會將 .net 物件轉換成可在網頁瀏覽器中顯示的 HTML。</span><span class="sxs-lookup"><span data-stu-id="79859-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="79859-111">您可以使用這個 Cmdlet 在網頁中顯示命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="79859-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="79859-112">您可以使用的參數來 `ConvertTo-Html` 選取物件屬性、指定表格或清單格式、指定 HTML 頁標題、在物件的前後新增文字，以及只傳回表格或清單片段，而不是 STRICT DTD 頁面。</span><span class="sxs-lookup"><span data-stu-id="79859-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="79859-113">當您將多個物件提交至時 `ConvertTo-Html` ，PowerShell 會根據您所提交之第一個物件的屬性，建立 (或列出) 的資料表。</span><span class="sxs-lookup"><span data-stu-id="79859-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="79859-114">如果剩餘的物件不具有其中一個指定的屬性，該物件的屬性值將會是空的儲存格。</span><span class="sxs-lookup"><span data-stu-id="79859-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="79859-115">如果其餘的物件有其他屬性，那些屬性值將不會包含在檔案中。</span><span class="sxs-lookup"><span data-stu-id="79859-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="79859-116">範例</span><span class="sxs-lookup"><span data-stu-id="79859-116">EXAMPLES</span></span>

### <span data-ttu-id="79859-117">範例1：建立網頁以顯示日期</span><span class="sxs-lookup"><span data-stu-id="79859-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="79859-118">此命令建立一個顯示目前日期之屬性的 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="79859-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="79859-119">它會使用 **InputObject** 參數將命令的結果提交 `Get-Date` 至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79859-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="79859-120">範例2：建立可顯示 PowerShell 別名的網頁</span><span class="sxs-lookup"><span data-stu-id="79859-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="79859-121">此命令會建立 HTML 網頁，以列出目前主控台中的 PowerShell 別名。</span><span class="sxs-lookup"><span data-stu-id="79859-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="79859-122">此命令會使用 `Get-Alias` Cmdlet 來取得別名。</span><span class="sxs-lookup"><span data-stu-id="79859-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="79859-123">它使用管線運算子 (`|`) 將別名傳送至 `ConvertTo-Html` Cmdlet，此 Cmdlet 會建立 HTML 網頁。</span><span class="sxs-lookup"><span data-stu-id="79859-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="79859-124">此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `aliases.htm` 。</span><span class="sxs-lookup"><span data-stu-id="79859-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="79859-125">範例3：建立可顯示 PowerShell 事件的網頁</span><span class="sxs-lookup"><span data-stu-id="79859-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="79859-126">此命令會建立一個名為 `pslog.htm` 的 HTML 網頁，以顯示本機電腦上 Windows PowerShell 事件記錄檔中的事件。</span><span class="sxs-lookup"><span data-stu-id="79859-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="79859-127">它會使用 `Get-EventLog` Cmdlet 取得 Windows PowerShell 記錄檔中的事件，然後使用管線運算子 () 將 `|` 事件傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79859-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="79859-128">此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `pslog.htm` 。</span><span class="sxs-lookup"><span data-stu-id="79859-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="79859-129">此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `pslog.htm` 。</span><span class="sxs-lookup"><span data-stu-id="79859-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="79859-130">範例4：建立網頁以顯示進程</span><span class="sxs-lookup"><span data-stu-id="79859-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="79859-131">這些命令建立並開啟一個 HTML 網頁，當中列出本機電腦上處理程序的名稱、路徑及公司。</span><span class="sxs-lookup"><span data-stu-id="79859-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="79859-132">第一個命令會使用 `Get-Process` Cmdlet 來取得代表電腦上執行之處理常式的物件。</span><span class="sxs-lookup"><span data-stu-id="79859-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="79859-133">此命令會使用管線運算子 (`|`) 將處理常式物件傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79859-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="79859-134">此命令會使用 **Property** 參數來選取要包含在資料表中之進程物件的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="79859-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="79859-135">命令使用 **title** 參數指定 HTML 網頁的標題。</span><span class="sxs-lookup"><span data-stu-id="79859-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="79859-136">此命令也會使用 `Out-File` Cmdlet 將產生的 HTML 傳送至名為 Proc.htm 的檔案。</span><span class="sxs-lookup"><span data-stu-id="79859-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="79859-137">第二個命令會使用 `Invoke-Item` Cmdlet `Proc.htm` 在預設瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="79859-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="79859-138">範例5：建立用來顯示服務物件的網頁</span><span class="sxs-lookup"><span data-stu-id="79859-138">Example 5: Create a web page to display service objects</span></span>

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

<span data-ttu-id="79859-139">此命令會建立 Cmdlet 所傳回之服務物件的 HTML 網頁 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="79859-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="79859-140">此命令會使用 **CssUri** 參數指定 HTML 網頁的級聯樣式表。</span><span class="sxs-lookup"><span data-stu-id="79859-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="79859-141">**CssUri** 參數會將其他 `<link rel="stylesheet" type="text/css" href="test.css">` 標記新增至產生的 HTML。</span><span class="sxs-lookup"><span data-stu-id="79859-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="79859-142">標記中的 HREF 屬性包含樣式表的名稱。</span><span class="sxs-lookup"><span data-stu-id="79859-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="79859-143">範例6：建立網頁以顯示服務物件</span><span class="sxs-lookup"><span data-stu-id="79859-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="79859-144">此命令會建立 Cmdlet 所傳回之服務物件的 HTML 網頁 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="79859-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="79859-145">命令使用 **As** 參數指定清單格式。</span><span class="sxs-lookup"><span data-stu-id="79859-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="79859-146">Cmdlet 會 `Out-File` 將產生的 HTML 傳送至檔案 `Services.htm` 。</span><span class="sxs-lookup"><span data-stu-id="79859-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="79859-147">範例7：建立目前日期的 web 資料表</span><span class="sxs-lookup"><span data-stu-id="79859-147">Example 7: Create a web table for the current date</span></span>

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

<span data-ttu-id="79859-148">此命令會使用 `ConvertTo-Html` 來產生目前日期的 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="79859-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="79859-149">此命令會使用 `Get-Date` Cmdlet 來取得目前的日期。</span><span class="sxs-lookup"><span data-stu-id="79859-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="79859-150">它使用管線運算子 (|) 將結果傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79859-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="79859-151">此 `ConvertTo-Html` 命令包含 **片段** 參數，此參數會將輸出限制為 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="79859-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="79859-152">因此，會省略 HTML 網頁的其他元素，例如 `<HEAD>` 和 `<BODY>` 標記。</span><span class="sxs-lookup"><span data-stu-id="79859-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="79859-153">範例8：建立可顯示 PowerShell 事件的網頁</span><span class="sxs-lookup"><span data-stu-id="79859-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="79859-154">此命令會使用 `Get-EventLog` Cmdlet 從 Windows PowerShell 事件記錄檔取得事件。</span><span class="sxs-lookup"><span data-stu-id="79859-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="79859-155">它使用管線運算子 (`|`) 將事件傳送至 `ConvertTo-Html` Cmdlet，以將事件轉換成 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="79859-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="79859-156">此 `ConvertTo-Html` 命令會使用 **Property** 參數，只選取事件 **的 ID** 、 **Level** 及 **Task** 屬性。</span><span class="sxs-lookup"><span data-stu-id="79859-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="79859-157">範例9：建立可顯示指定服務的網頁</span><span class="sxs-lookup"><span data-stu-id="79859-157">Example 9: Create a web page to display specified services</span></span>

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

<span data-ttu-id="79859-158">此命令會建立並開啟一個網頁，顯示電腦上以開頭的服務。它使用的 **Title** 、 **Body** 、 **PreContent** 和 **PostContent** 參數 `ConvertTo-Html` 來自訂輸出。</span><span class="sxs-lookup"><span data-stu-id="79859-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="79859-159">命令的第一個部分 `Get-Service` 會使用 Cmdlet 來取得電腦上以開頭的服務。此命令會使用管線運算子 (`|`) 將結果傳送至 `ConvertTo-Html` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79859-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="79859-160">此命令也會使用 `Out-File` Cmdlet 將輸出傳送至 Services.htm 的檔案。</span><span class="sxs-lookup"><span data-stu-id="79859-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="79859-161">分號 (`;`) 結束第一個命令並啟動第二個命令，此命令會使用 `Invoke-Item` Cmdlet `Services.htm` 在預設瀏覽器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="79859-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

## <span data-ttu-id="79859-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="79859-162">PARAMETERS</span></span>

### <span data-ttu-id="79859-163">-As</span><span class="sxs-lookup"><span data-stu-id="79859-163">-As</span></span>

<span data-ttu-id="79859-164">決定要將物件的格式設定為表格或清單。</span><span class="sxs-lookup"><span data-stu-id="79859-164">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="79859-165">有效的值為 **資料表** 和 **清單** 。</span><span class="sxs-lookup"><span data-stu-id="79859-165">Valid values are **Table** and **List** .</span></span> <span data-ttu-id="79859-166">預設值為 **Table** 。</span><span class="sxs-lookup"><span data-stu-id="79859-166">The default value is **Table** .</span></span>

<span data-ttu-id="79859-167">**資料表** 值會產生類似于 PowerShell 資料表格式的 HTML 資料表。</span><span class="sxs-lookup"><span data-stu-id="79859-167">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="79859-168">標題列會顯示屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="79859-168">The header row displays the property names.</span></span> <span data-ttu-id="79859-169">每個表格列皆代表一個物件，並會顯示該物件每個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="79859-169">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="79859-170">**List** 值會為每個類似于 PowerShell 清單格式的物件產生兩個數據行的 HTML 資料表。</span><span class="sxs-lookup"><span data-stu-id="79859-170">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="79859-171">第一個資料行顯示內容名稱。</span><span class="sxs-lookup"><span data-stu-id="79859-171">The first column displays the property name.</span></span> <span data-ttu-id="79859-172">第二欄顯示內容值。</span><span class="sxs-lookup"><span data-stu-id="79859-172">The second column displays the property value.</span></span>

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

### <span data-ttu-id="79859-173">-Body</span><span class="sxs-lookup"><span data-stu-id="79859-173">-Body</span></span>

<span data-ttu-id="79859-174">指定要在開頭 `<BODY>` 標記之後新增的文字。</span><span class="sxs-lookup"><span data-stu-id="79859-174">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="79859-175">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="79859-175">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="79859-176">-CssUri</span><span class="sxs-lookup"><span data-stu-id="79859-176">-CssUri</span></span>

<span data-ttu-id="79859-177">指定套用到 HTML 檔案之階層式樣式表 (CSS) 的統一資源識別項 (URI)。</span><span class="sxs-lookup"><span data-stu-id="79859-177">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="79859-178">URI 包含在輸出中的樣式表連結內。</span><span class="sxs-lookup"><span data-stu-id="79859-178">The URI is included in a style sheet link in the output.</span></span>

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

### <span data-ttu-id="79859-179">-Fragment</span><span class="sxs-lookup"><span data-stu-id="79859-179">-Fragment</span></span>

<span data-ttu-id="79859-180">只產生 HTML 表格。</span><span class="sxs-lookup"><span data-stu-id="79859-180">Generates only an HTML table.</span></span> <span data-ttu-id="79859-181">將會省略 HTML、HEAD、TITLE 及 BODY 標記。</span><span class="sxs-lookup"><span data-stu-id="79859-181">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

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

### <span data-ttu-id="79859-182">-Head</span><span class="sxs-lookup"><span data-stu-id="79859-182">-Head</span></span>

<span data-ttu-id="79859-183">指定 `<HEAD>` 標記的內容。</span><span class="sxs-lookup"><span data-stu-id="79859-183">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="79859-184">預設為 `<title\>HTML TABLE</title>`。</span><span class="sxs-lookup"><span data-stu-id="79859-184">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="79859-185">如果您使用 **Head** 參數，則會忽略 **Title** 參數。</span><span class="sxs-lookup"><span data-stu-id="79859-185">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

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

### <span data-ttu-id="79859-186">-InputObject</span><span class="sxs-lookup"><span data-stu-id="79859-186">-InputObject</span></span>

<span data-ttu-id="79859-187">指定要以 HTML 呈現的物件。</span><span class="sxs-lookup"><span data-stu-id="79859-187">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="79859-188">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="79859-188">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="79859-189">如果您使用此參數提交多個物件（例如電腦上的所有服務），則 `ConvertTo-Html` 會建立一個資料表，以顯示集合或物件陣列的屬性。</span><span class="sxs-lookup"><span data-stu-id="79859-189">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="79859-190">若要建立個別物件的表格，請使用管線運算子將物件輸送至 `ConvertTo-Html` 。</span><span class="sxs-lookup"><span data-stu-id="79859-190">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="79859-191">-PostContent</span><span class="sxs-lookup"><span data-stu-id="79859-191">-PostContent</span></span>

<span data-ttu-id="79859-192">指定要在結尾 `</TABLE>` 標記之後新增的文字。</span><span class="sxs-lookup"><span data-stu-id="79859-192">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="79859-193">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="79859-193">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="79859-194">-PreContent</span><span class="sxs-lookup"><span data-stu-id="79859-194">-PreContent</span></span>

<span data-ttu-id="79859-195">指定要在開頭 `<TABLE>` 標記之前新增的文字。</span><span class="sxs-lookup"><span data-stu-id="79859-195">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="79859-196">該位置預設不會有任何文字。</span><span class="sxs-lookup"><span data-stu-id="79859-196">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="79859-197">-Property</span><span class="sxs-lookup"><span data-stu-id="79859-197">-Property</span></span>

<span data-ttu-id="79859-198">將物件的指定屬性包含在 HTML 中。</span><span class="sxs-lookup"><span data-stu-id="79859-198">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="79859-199">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="79859-199">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="79859-200">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="79859-200">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="79859-201">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="79859-201">Valid key-value pairs are:</span></span>

- <span data-ttu-id="79859-202">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="79859-202">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="79859-203">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="79859-203">FormatString - `<string>`</span></span>
- <span data-ttu-id="79859-204">寬度- `<int32>` -必須大於 `0`</span><span class="sxs-lookup"><span data-stu-id="79859-204">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="79859-205">對齊-值可以是 `Left` 、 `Center` 或 `Right`</span><span class="sxs-lookup"><span data-stu-id="79859-205">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="79859-206">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="79859-206">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="79859-207">-Title</span><span class="sxs-lookup"><span data-stu-id="79859-207">-Title</span></span>

<span data-ttu-id="79859-208">指定 HTML 檔案的標題，也就是出現在 `<TITLE>` 標記之間的文字。</span><span class="sxs-lookup"><span data-stu-id="79859-208">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

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

### <span data-ttu-id="79859-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79859-209">CommonParameters</span></span>

<span data-ttu-id="79859-210">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="79859-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79859-211">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="79859-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79859-212">輸入</span><span class="sxs-lookup"><span data-stu-id="79859-212">INPUTS</span></span>

### <span data-ttu-id="79859-213">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="79859-213">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="79859-214">您可以透過管道將任何 .NET 物件傳送至 `ConvertTo-Html` 。</span><span class="sxs-lookup"><span data-stu-id="79859-214">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="79859-215">輸出</span><span class="sxs-lookup"><span data-stu-id="79859-215">OUTPUTS</span></span>

### <span data-ttu-id="79859-216">System.string 或 System.Xml.Xml檔</span><span class="sxs-lookup"><span data-stu-id="79859-216">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="79859-217">`ConvertTo-Html` 傳回組成有效 HTML 的一連串字串。</span><span class="sxs-lookup"><span data-stu-id="79859-217">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="79859-218">注意</span><span class="sxs-lookup"><span data-stu-id="79859-218">NOTES</span></span>

<span data-ttu-id="79859-219">若要使用此 Cmdlet，請使用管線將一或多個物件傳送至 Cmdlet，或使用 **InputObject** 參數來指定物件。</span><span class="sxs-lookup"><span data-stu-id="79859-219">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="79859-220">當輸入是由多個物件組成時，這兩個方法的輸出會非常不一樣。</span><span class="sxs-lookup"><span data-stu-id="79859-220">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="79859-221">當您使用管線將多個物件傳送至 Cmdlet 時，PowerShell 會一次將物件傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79859-221">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="79859-222">因此， `ConvertTo-Html` 會建立顯示個別物件的資料表。</span><span class="sxs-lookup"><span data-stu-id="79859-222">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="79859-223">例如，如果您使用管線將電腦上的處理常式傳送至 `ConvertTo-Html` ，則產生的表格會顯示所有的處理常式。</span><span class="sxs-lookup"><span data-stu-id="79859-223">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="79859-224">當您使用 **InputObject** 參數提交多個物件時，會 `ConvertTo-Html` 以集合或陣列的形式接收這些物件。</span><span class="sxs-lookup"><span data-stu-id="79859-224">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="79859-225">因此，它會建立顯示陣列及其屬性 (而非顯示陣列中的項目) 的表格。</span><span class="sxs-lookup"><span data-stu-id="79859-225">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="79859-226">例如，如果您使用 **InputObject** 將電腦上的處理常式提交至 `ConvertTo-Html` ，則產生的資料表會顯示物件陣列和其屬性。</span><span class="sxs-lookup"><span data-stu-id="79859-226">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="79859-227">為了符合 XHTML 嚴格 DTD，會據以修改 DOCTYPE 標記：</span><span class="sxs-lookup"><span data-stu-id="79859-227">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="79859-228">相關連結</span><span class="sxs-lookup"><span data-stu-id="79859-228">RELATED LINKS</span></span>

[<span data-ttu-id="79859-229">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="79859-229">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="79859-230">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="79859-230">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="79859-231">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="79859-231">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="79859-232">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="79859-232">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="79859-233">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="79859-233">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="79859-234">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="79859-234">Import-Clixml</span></span>](Import-Clixml.md)
