---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 543c2b683ca3631e2e05f57d9c70ff4455071e4b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205052"
---
# <span data-ttu-id="94666-103">Get-Process</span><span class="sxs-lookup"><span data-stu-id="94666-103">Get-Process</span></span>

## <span data-ttu-id="94666-104">概要</span><span class="sxs-lookup"><span data-stu-id="94666-104">SYNOPSIS</span></span>
<span data-ttu-id="94666-105">取得在本機電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-105">Gets the processes that are running on the local computer.</span></span>

## <span data-ttu-id="94666-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="94666-106">SYNTAX</span></span>

### <span data-ttu-id="94666-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="94666-107">Name (Default)</span></span>

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="94666-108">NameWithUserName</span><span class="sxs-lookup"><span data-stu-id="94666-108">NameWithUserName</span></span>

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="94666-109">Id</span><span class="sxs-lookup"><span data-stu-id="94666-109">Id</span></span>

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="94666-110">IdWithUserName</span><span class="sxs-lookup"><span data-stu-id="94666-110">IdWithUserName</span></span>

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### <span data-ttu-id="94666-111">InputObject</span><span class="sxs-lookup"><span data-stu-id="94666-111">InputObject</span></span>

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### <span data-ttu-id="94666-112">InputObjectWithUserName</span><span class="sxs-lookup"><span data-stu-id="94666-112">InputObjectWithUserName</span></span>

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## <span data-ttu-id="94666-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="94666-113">DESCRIPTION</span></span>

<span data-ttu-id="94666-114">`Get-Process`Cmdlet 會取得本機電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-114">The `Get-Process` cmdlet gets the processes on a local computer.</span></span>

<span data-ttu-id="94666-115">如果沒有參數，這個 Cmdlet 會取得本機電腦上的所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-115">Without parameters, this cmdlet gets all of the processes on the local computer.</span></span>
<span data-ttu-id="94666-116">您也可以使用進程名稱或處理序識別碼 (PID 來指定特定處理常式) 或透過管線將處理常式物件傳遞至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94666-116">You can also specify a particular process by process name or process ID (PID) or pass a process object through the pipeline to this cmdlet.</span></span>

<span data-ttu-id="94666-117">根據預設，此 Cmdlet 會傳回包含此進程之詳細資訊的處理常式物件，並支援可讓您啟動和停止進程的方法。</span><span class="sxs-lookup"><span data-stu-id="94666-117">By default, this cmdlet returns a process object that has detailed information about the process and supports methods that let you start and stop the process.</span></span>
<span data-ttu-id="94666-118">您也可以使用 Cmdlet 的參數 `Get-Process` 來取得在處理常式中執行之程式的檔案版本資訊，以及取得處理常式所載入的模組。</span><span class="sxs-lookup"><span data-stu-id="94666-118">You can also use the parameters of the `Get-Process` cmdlet to get file version information for the program that runs in the process and to get the modules that the process loaded.</span></span>

## <span data-ttu-id="94666-119">範例</span><span class="sxs-lookup"><span data-stu-id="94666-119">EXAMPLES</span></span>

### <span data-ttu-id="94666-120">範例1：取得本機電腦上所有使用中進程的清單</span><span class="sxs-lookup"><span data-stu-id="94666-120">Example 1: Get a list of all active processes on the local computer</span></span>

```powershell
Get-Process
```

<span data-ttu-id="94666-121">此命令會取得在本機電腦上執行之所有使用中進程的清單。</span><span class="sxs-lookup"><span data-stu-id="94666-121">This command gets a list of all active processes running on the local computer.</span></span>
<span data-ttu-id="94666-122">如需每個資料行的定義，請參閱 [附注](#notes) 一節。</span><span class="sxs-lookup"><span data-stu-id="94666-122">For a definition of each column, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="94666-123">範例2：取得一或多個處理常式的所有可用資料</span><span class="sxs-lookup"><span data-stu-id="94666-123">Example 2: Get all available data about one or more processes</span></span>

```powershell
Get-Process winword, explorer | Format-List *
```

<span data-ttu-id="94666-124">此命令取得電腦上 Winword 和 Explorer 處理程序的所有可用相關資料。</span><span class="sxs-lookup"><span data-stu-id="94666-124">This command gets all available data about the Winword and Explorer processes on the computer.</span></span>
<span data-ttu-id="94666-125">它會使用 **Name** 參數來指定處理常式，但會省略選擇性的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="94666-125">It uses the **Name** parameter to specify the processes, but it omits the optional parameter name.</span></span>
<span data-ttu-id="94666-126">管線運算子會將 `|` 資料傳遞至 `Format-List` Cmdlet，此 Cmdlet 會顯示 `*` Winword 和 Explorer 處理常式物件的所有可用屬性。</span><span class="sxs-lookup"><span data-stu-id="94666-126">The pipeline operator `|` passes the data to the `Format-List` cmdlet, which displays all available properties `*` of the Winword and Explorer process objects.</span></span>

<span data-ttu-id="94666-127">您也可以依處理程序識別碼來識別處理程序。</span><span class="sxs-lookup"><span data-stu-id="94666-127">You can also identify the processes by their process IDs.</span></span>
<span data-ttu-id="94666-128">例如， `Get-Process -Id 664, 2060` 。</span><span class="sxs-lookup"><span data-stu-id="94666-128">For instance, `Get-Process -Id 664, 2060`.</span></span>

### <span data-ttu-id="94666-129">範例3：取得工作集大於指定大小的所有處理常式</span><span class="sxs-lookup"><span data-stu-id="94666-129">Example 3: Get all processes with a working set greater than a specified size</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

<span data-ttu-id="94666-130">此命令取得工作集大於 20 MB 的所有處理程序。</span><span class="sxs-lookup"><span data-stu-id="94666-130">This command gets all processes that have a working set greater than 20 MB.</span></span>
<span data-ttu-id="94666-131">它會使用 `Get-Process`  Cmdlet 來取得所有執行中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-131">It uses the `Get-Process`  cmdlet to get all running processes.</span></span>
<span data-ttu-id="94666-132">管線運算子會將 `|` 處理常式物件傳遞至 `Where-Object` Cmdlet，此 Cmdlet 只會選取值大於20000000個位元組的物件給工作 **WorkingSet** 人員屬性。</span><span class="sxs-lookup"><span data-stu-id="94666-132">The pipeline operator `|` passes the process objects to the `Where-Object` cmdlet, which selects only the object with a value greater than 20,000,000 bytes for the **WorkingSet** property.</span></span>

<span data-ttu-id="94666-133">集 **量是處理** 程式物件的眾多屬性之一。</span><span class="sxs-lookup"><span data-stu-id="94666-133">**WorkingSet** is one of many properties of process objects.</span></span>
<span data-ttu-id="94666-134">若要查看所有屬性，請輸入 `Get-Process | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="94666-134">To see all of the properties, type `Get-Process | Get-Member`.</span></span>
<span data-ttu-id="94666-135">根據預設，所有數量屬性都是以位元組為單位，即使預設顯示是以 KB 和 MB 來列示它們。</span><span class="sxs-lookup"><span data-stu-id="94666-135">By default, the values of all amount properties are in bytes, even though the default display lists them in kilobytes and megabytes.</span></span>

### <span data-ttu-id="94666-136">範例4：根據優先順序列出電腦上的進程</span><span class="sxs-lookup"><span data-stu-id="94666-136">Example 4: List processes on the computer in groups based on priority</span></span>

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

<span data-ttu-id="94666-137">這些命令會根據其優先順序類別，將電腦上的處理常式列示在群組中。</span><span class="sxs-lookup"><span data-stu-id="94666-137">These commands list the processes on the computer in groups based on their priority class.</span></span>
<span data-ttu-id="94666-138">第一個命令會取得電腦上的所有處理常式，然後將它們儲存在 `$A` 變數中。</span><span class="sxs-lookup"><span data-stu-id="94666-138">The first command gets all the processes on the computer and then stores them in the `$A` variable.</span></span>

<span data-ttu-id="94666-139">第二個命令會使用管線將儲存在變數中的 **處理** 程式物件傳送 `$A` 至 `Get-Process` Cmdlet，然後傳送至 `Format-Table` Cmdlet，以使用 **優先權** 視圖來格式化處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-139">The second command pipes the **Process** object stored in the `$A` variable to the `Get-Process` cmdlet, then to the `Format-Table` cmdlet, which formats the processes by using the **Priority** view.</span></span>

<span data-ttu-id="94666-140">**優先權** 視圖和其他視圖都是在 PowerShell 主目錄 () 中的 .ps1xml 格式檔案中定義 `$pshome` 。</span><span class="sxs-lookup"><span data-stu-id="94666-140">The **Priority** view, and other views, are defined in the PS1XML format files in the PowerShell home directory (`$pshome`).</span></span>

### <span data-ttu-id="94666-141">範例5：將屬性新增至標準 Get-Process 輸出顯示</span><span class="sxs-lookup"><span data-stu-id="94666-141">Example 5: Add a property to the standard Get-Process output display</span></span>

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

<span data-ttu-id="94666-142">這個範例會提供 `Format-Table` 將 **MachineName** 屬性新增至標準 `Get-Process` 輸出顯示的命令。</span><span class="sxs-lookup"><span data-stu-id="94666-142">This example provides a `Format-Table` command that adds the **MachineName** property to the standard `Get-Process` output display.</span></span>

### <span data-ttu-id="94666-143">範例6：取得處理常式的版本資訊</span><span class="sxs-lookup"><span data-stu-id="94666-143">Example 6: Get version information for a process</span></span>

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

<span data-ttu-id="94666-144">此命令會使用 **FileVersionInfo** 參數來取得 PowerShell 處理常式的主要模組 pwsh.exe 檔案的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="94666-144">This command uses the **FileVersionInfo** parameter to get the version information for the pwsh.exe file that is the main module for the PowerShell process.</span></span>

<span data-ttu-id="94666-145">若要在 Windows Vista 和更新版本的 Windows 上，使用您未擁有的進程來執行此命令，您必須使用 [以系統管理員身分執行] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="94666-145">To run this command with processes that you do not own on Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="94666-146">範例7：取得以指定進程載入的模組</span><span class="sxs-lookup"><span data-stu-id="94666-146">Example 7: Get modules loaded with the specified process</span></span>

```powershell
Get-Process SQL* -Module
```

<span data-ttu-id="94666-147">此命令會使用 **Module** 參數取得處理常式所載入的模組。</span><span class="sxs-lookup"><span data-stu-id="94666-147">This command uses the **Module** parameter to get the modules that have been loaded by the process.</span></span>
<span data-ttu-id="94666-148">此命令會取得名稱開頭為 SQL 之進程的模組。</span><span class="sxs-lookup"><span data-stu-id="94666-148">This command gets the modules for the processes that have names that begin with SQL.</span></span>

<span data-ttu-id="94666-149">若要在 Windows Vista 和更新版本的 Windows 上，使用您未擁有的進程來執行此命令，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="94666-149">To run this command on Windows Vista and later versions of Windows with processes that you do not own, you must start PowerShell with the Run as administrator option.</span></span>

### <span data-ttu-id="94666-150">範例8：尋找進程的擁有者</span><span class="sxs-lookup"><span data-stu-id="94666-150">Example 8: Find the owner of a process</span></span>

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

<span data-ttu-id="94666-151">此命令示範如何尋找處理程序的擁有者。</span><span class="sxs-lookup"><span data-stu-id="94666-151">This command shows how to find the owner of a process.</span></span>
<span data-ttu-id="94666-152">在 Windows 中， **IncludeUserName** 參數需要提高的使用者權限 (以系統管理員身分執行) 。</span><span class="sxs-lookup"><span data-stu-id="94666-152">On Windows, the **IncludeUserName** parameter requires elevated user rights (Run as Administrator).</span></span>
<span data-ttu-id="94666-153">輸出顯示擁有者為 Domain01\user01。</span><span class="sxs-lookup"><span data-stu-id="94666-153">The output reveals that the owner is Domain01\user01.</span></span>

### <span data-ttu-id="94666-154">範例9：使用自動變數來識別裝載目前會話的進程</span><span class="sxs-lookup"><span data-stu-id="94666-154">Example 9: Use an automatic variable to identify the process hosting the current session</span></span>

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

<span data-ttu-id="94666-155">這些命令會示範如何使用 `$PID` 自動變數來識別裝載目前 PowerShell 會話的處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-155">These commands show how to use the `$PID` automatic variable to identify the process that is hosting the current PowerShell session.</span></span>
<span data-ttu-id="94666-156">您可以使用這個方法來區別主機進程與其他您可能想要停止或關閉的 PowerShell 進程。</span><span class="sxs-lookup"><span data-stu-id="94666-156">You can use this method to distinguish the host process from other PowerShell processes that you might want to stop or close.</span></span>

<span data-ttu-id="94666-157">第一個命令會取得目前會話中的所有 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-157">The first command gets all of the PowerShell processes in the current session.</span></span>

<span data-ttu-id="94666-158">第二個命令會取得裝載目前會話的 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="94666-158">The second command gets the PowerShell process that is hosting the current session.</span></span>

### <span data-ttu-id="94666-159">範例10：取得具有主視窗標題的所有處理常式，並將它們顯示在資料表中</span><span class="sxs-lookup"><span data-stu-id="94666-159">Example 10: Get all processes that have a main window title and display them in a table</span></span>

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

<span data-ttu-id="94666-160">此命令取得具有主視窗標題的所有處理程序，並將它們顯示在含有處理程序識別碼和處理程序名稱的表格中。</span><span class="sxs-lookup"><span data-stu-id="94666-160">This command gets all the processes that have a main window title, and it displays them in a table with the process ID and the process name.</span></span>

<span data-ttu-id="94666-161">**MainWindowTitle** 屬性只是傳回之 **處理** 程式物件的許多實用屬性之一 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="94666-161">The **mainWindowTitle** property is just one of many useful properties of the **Process** object that `Get-Process` returns.</span></span>
<span data-ttu-id="94666-162">若要查看所有屬性，請使用管線將命令的結果傳送 `Get-Process` 至 `Get-Member` Cmdlet `Get-Process | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="94666-162">To view all of the properties, pipe the results of a `Get-Process` command to the `Get-Member` cmdlet `Get-Process | Get-Member`.</span></span>

## <span data-ttu-id="94666-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="94666-163">PARAMETERS</span></span>

### <span data-ttu-id="94666-164">-FileVersionInfo</span><span class="sxs-lookup"><span data-stu-id="94666-164">-FileVersionInfo</span></span>

<span data-ttu-id="94666-165">指出此 Cmdlet 會取得在處理常式中執行之程式的檔案版本資訊。</span><span class="sxs-lookup"><span data-stu-id="94666-165">Indicates that this cmdlet gets the file version information for the program that runs in the process.</span></span>

<span data-ttu-id="94666-166">在 Windows Vista 和更新版本的 Windows 上，您必須使用 [以系統管理員身分執行] 選項開啟 PowerShell，才能在不是您所擁有的處理常式上使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="94666-166">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="94666-167">若要取得遠端電腦上處理常式的檔案版本資訊，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94666-167">To get file version information for a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="94666-168">使用這個參數相當於取得每個處理常式物件的 **mainmodule.fileversioninfo. FileVersionInfo** 屬性。</span><span class="sxs-lookup"><span data-stu-id="94666-168">Using this parameter is equivalent to getting the **MainModule.FileVersionInfo** property of each process object.</span></span>
<span data-ttu-id="94666-169">當您使用這個參數時， `Get-Process` 會傳回 **FileVersionInfo** 物件 FileVersionInfo，而不是處理 **程式** 物件。</span><span class="sxs-lookup"><span data-stu-id="94666-169">When you use this parameter, `Get-Process` returns a **FileVersionInfo** object **System.Diagnostics.FileVersionInfo** , not a process object.</span></span>
<span data-ttu-id="94666-170">因此，您無法使用管線將命令的輸出傳送到預期處理常式物件的 Cmdlet，例如 `Stop-Process` 。</span><span class="sxs-lookup"><span data-stu-id="94666-170">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94666-171">-Id</span><span class="sxs-lookup"><span data-stu-id="94666-171">-Id</span></span>

<span data-ttu-id="94666-172">依處理程序識別碼 (PID) 指定一個或多個處理程序。</span><span class="sxs-lookup"><span data-stu-id="94666-172">Specifies one or more processes by process ID (PID).</span></span>
<span data-ttu-id="94666-173">若要指定多個識別碼，請使用逗號來分隔識別碼。</span><span class="sxs-lookup"><span data-stu-id="94666-173">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="94666-174">若要尋找處理程序的 PID，請輸入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="94666-174">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="94666-175">-IncludeUserName</span><span class="sxs-lookup"><span data-stu-id="94666-175">-IncludeUserName</span></span>

<span data-ttu-id="94666-176">指出會傳回 **進程** 物件的使用者名稱值與命令的結果。</span><span class="sxs-lookup"><span data-stu-id="94666-176">Indicates that the UserName value of the **Process** object is returned with results of the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94666-177">-InputObject</span><span class="sxs-lookup"><span data-stu-id="94666-177">-InputObject</span></span>

<span data-ttu-id="94666-178">指定一個或多個處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="94666-178">Specifies one or more process objects.</span></span>
<span data-ttu-id="94666-179">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="94666-179">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="94666-180">-Module</span><span class="sxs-lookup"><span data-stu-id="94666-180">-Module</span></span>

<span data-ttu-id="94666-181">指出此 Cmdlet 會取得處理常式所載入的模組。</span><span class="sxs-lookup"><span data-stu-id="94666-181">Indicates that this cmdlet gets the modules that have been loaded by the processes.</span></span>

<span data-ttu-id="94666-182">在 Windows Vista 和更新版本的 Windows 上，您必須使用 [以系統管理員身分執行] 選項開啟 PowerShell，才能在不是您所擁有的處理常式上使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="94666-182">On Windows Vista and later versions of Windows, you must open PowerShell with the Run as administrator option to use this parameter on processes that you do not own.</span></span>

<span data-ttu-id="94666-183">若要取得遠端電腦上的處理常式所載入的模組，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94666-183">To get the modules that have been loaded by a process on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="94666-184">這個參數相當於取得每個處理常式物件的 **模組** 屬性。</span><span class="sxs-lookup"><span data-stu-id="94666-184">This parameter is equivalent to getting the **Modules** property of each process object.</span></span>
<span data-ttu-id="94666-185">當您使用此參數時，此 Cmdlet 會傳回 **ProcessModule** 物件 ProcessModule，而不是處理 **程式** 物件。</span><span class="sxs-lookup"><span data-stu-id="94666-185">When you use this parameter, this cmdlet returns a **ProcessModule** object **System.Diagnostics.ProcessModule** , not a process object.</span></span>
<span data-ttu-id="94666-186">因此，您無法使用管線將命令的輸出傳送到預期處理常式物件的 Cmdlet，例如 `Stop-Process` 。</span><span class="sxs-lookup"><span data-stu-id="94666-186">So, you cannot pipe the output of the command to a cmdlet that expects a process object, such as `Stop-Process`.</span></span>

<span data-ttu-id="94666-187">當您在同一個命令中同時使用 *Module* 和 **FileVersionInfo** 參數時，此 Cmdlet 會傳回 **FileVersionInfo** 物件，其中包含所有模組之檔案版本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="94666-187">When you use both the *Module* and **FileVersionInfo** parameters in the same command, this cmdlet returns a **FileVersionInfo** object with information about the file version of all modules.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94666-188">-Name</span><span class="sxs-lookup"><span data-stu-id="94666-188">-Name</span></span>

<span data-ttu-id="94666-189">依處理程序名稱指定一個或多個處理程序。</span><span class="sxs-lookup"><span data-stu-id="94666-189">Specifies one or more processes by process name.</span></span>
<span data-ttu-id="94666-190">您可以輸入多個處理程序名稱 (以逗號分隔) 及使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="94666-190">You can type multiple process names (separated by commas) and use wildcard characters.</span></span>
<span data-ttu-id="94666-191">參數名稱 ("Name") 為選擇性。</span><span class="sxs-lookup"><span data-stu-id="94666-191">The parameter name ("Name") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="94666-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94666-192">CommonParameters</span></span>

<span data-ttu-id="94666-193">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="94666-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94666-194">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="94666-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="94666-195">輸入</span><span class="sxs-lookup"><span data-stu-id="94666-195">INPUTS</span></span>

### <span data-ttu-id="94666-196">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="94666-196">System.Diagnostics.Process</span></span>

<span data-ttu-id="94666-197">您可以使用管線將處理程序物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94666-197">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="94666-198">輸出</span><span class="sxs-lookup"><span data-stu-id="94666-198">OUTPUTS</span></span>

### <span data-ttu-id="94666-199">FileVersionInfo，ProcessModule 的程式，系統診斷。</span><span class="sxs-lookup"><span data-stu-id="94666-199">System.Diagnostics.Process, System.Diagnostics.FileVersionInfo, System.Diagnostics.ProcessModule</span></span>

<span data-ttu-id="94666-200">根據預設，此 Cmdlet 會傳回 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="94666-200">By default, this cmdlet returns a **System.Diagnostics.Process** object.</span></span>
<span data-ttu-id="94666-201">如果您使用 **FileVersionInfo** 參數，它會傳回 **FileVersionInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="94666-201">If you use the **FileVersionInfo** parameter, it returns a **System.Diagnostics.FileVersionInfo** object.</span></span>
<span data-ttu-id="94666-202">如果您使用 **Module** 參數，但沒有 **FileVersionInfo** 參數，則會傳回 **ProcessModule** 物件。</span><span class="sxs-lookup"><span data-stu-id="94666-202">If you use the **Module** parameter, without the **FileVersionInfo** parameter, it returns a **System.Diagnostics.ProcessModule** object.</span></span>

## <span data-ttu-id="94666-203">注意</span><span class="sxs-lookup"><span data-stu-id="94666-203">NOTES</span></span>

- <span data-ttu-id="94666-204">您也可以透過內建的別名（ps 和 gps）來參考這個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="94666-204">You can also refer to this cmdlet by its built-in aliases, ps and gps.</span></span> <span data-ttu-id="94666-205">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="94666-205">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="94666-206">在執行64位版 Windows 的電腦上，64位版本的 PowerShell 只會取得64位的進程模組，而32位版本的 PowerShell 只會取得32位的進程模組。</span><span class="sxs-lookup"><span data-stu-id="94666-206">On computers that are running a 64-bit version of Windows, the 64-bit version of PowerShell gets only 64-bit process modules and the 32-bit version of PowerShell gets only 32-bit process modules.</span></span>
- <span data-ttu-id="94666-207">您可以在 PowerShell 中使用 Windows Management Instrumentation (WMI) Win32_Process 物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="94666-207">You can use the properties and methods of the Windows Management Instrumentation (WMI) Win32_Process object in PowerShell.</span></span> <span data-ttu-id="94666-208">如需詳細資訊，請參閱 `Get-WmiObject` 和 WMI SDK。</span><span class="sxs-lookup"><span data-stu-id="94666-208">For information, see `Get-WmiObject` and the WMI SDK.</span></span>
- <span data-ttu-id="94666-209">處理程序的預設顯示是一個包含下列欄位的表格。</span><span class="sxs-lookup"><span data-stu-id="94666-209">The default display of a process is a table that includes the following columns.</span></span> <span data-ttu-id="94666-210">如需處理常式物件的所有屬性描述，請參閱 MSDN library 中的 [處理常式屬性](/dotnet/api/system.diagnostics.process) 。</span><span class="sxs-lookup"><span data-stu-id="94666-210">For a description of all of the properties of process objects, see [Process Properties](/dotnet/api/system.diagnostics.process) in the MSDN library.</span></span>
  - <span data-ttu-id="94666-211">控制碼：進程已開啟的控制碼數目。</span><span class="sxs-lookup"><span data-stu-id="94666-211">Handles: The number of handles that the process has opened.</span></span>
  - <span data-ttu-id="94666-212">NPM (K) ：進程正在使用的非分頁式記憶體數量（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="94666-212">NPM(K): The amount of non-paged memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="94666-213">PM (K) ：進程正在使用的可分頁記憶體數量（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="94666-213">PM(K): The amount of pageable memory that the process is using, in kilobytes.</span></span>
  - <span data-ttu-id="94666-214">WS (K) ：進程的工作集大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="94666-214">WS(K): The size of the working set of the process, in kilobytes.</span></span>
    <span data-ttu-id="94666-215">工作集是由處理程序最近參照的記憶體分頁組成。</span><span class="sxs-lookup"><span data-stu-id="94666-215">The working set consists of the pages of memory that were recently referenced by the process.</span></span>
  - <span data-ttu-id="94666-216">VM (M) ：進程正在使用的虛擬記憶體數量（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="94666-216">VM(M): The amount of virtual memory that the process is using, in megabytes.</span></span>
    <span data-ttu-id="94666-217">虛擬記憶體包括磁碟上分頁檔案中的儲存體。</span><span class="sxs-lookup"><span data-stu-id="94666-217">Virtual memory includes storage in the paging files on disk.</span></span>
  - <span data-ttu-id="94666-218">CPU (s) ：進程已在所有處理器上使用的處理器時間量（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="94666-218">CPU(s): The amount of processor time that the process has used on all processors, in seconds.</span></span>
  - <span data-ttu-id="94666-219">識別碼：進程的處理序識別碼 (PID) 。</span><span class="sxs-lookup"><span data-stu-id="94666-219">ID: The process ID (PID) of the process.</span></span>
  - <span data-ttu-id="94666-220">ProcessName：進程的名稱。</span><span class="sxs-lookup"><span data-stu-id="94666-220">ProcessName: The name of the process.</span></span>
    <span data-ttu-id="94666-221">如需處理程序相關概念的說明，請參閱 [說明及支援中心] 中的 [詞彙] 和 [工作管理員] 的 [說明]。</span><span class="sxs-lookup"><span data-stu-id="94666-221">For explanations of the concepts related to processes, see the Glossary in Help and Support Center and the Help for Task Manager.</span></span>
- <span data-ttu-id="94666-222">您也可以使用所提供之進程的內建替代視圖 `Format-Table` ，例如 **StartTime** 和 **Priority** ，也可以設計自己的觀點。</span><span class="sxs-lookup"><span data-stu-id="94666-222">You can also use the built-in alternate views of the processes available with `Format-Table`, such as **StartTime** and **Priority** , and you can design your own views.</span></span>

## <span data-ttu-id="94666-223">相關連結</span><span class="sxs-lookup"><span data-stu-id="94666-223">RELATED LINKS</span></span>

[<span data-ttu-id="94666-224">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="94666-224">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="94666-225">Get-Process</span><span class="sxs-lookup"><span data-stu-id="94666-225">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="94666-226">Start-Process</span><span class="sxs-lookup"><span data-stu-id="94666-226">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="94666-227">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="94666-227">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="94666-228">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="94666-228">Wait-Process</span></span>](Wait-Process.md)

