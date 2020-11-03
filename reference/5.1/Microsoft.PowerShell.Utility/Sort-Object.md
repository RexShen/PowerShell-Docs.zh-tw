---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 1d27641f94d82b85bab694b392c0f09bb3265517
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205904"
---
# <span data-ttu-id="3232d-103">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-103">Sort-Object</span></span>

## <span data-ttu-id="3232d-104">概要</span><span class="sxs-lookup"><span data-stu-id="3232d-104">SYNOPSIS</span></span>
<span data-ttu-id="3232d-105">依屬性值排序物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-105">Sorts objects by property values.</span></span>

## <span data-ttu-id="3232d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3232d-106">SYNTAX</span></span>

### <span data-ttu-id="3232d-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="3232d-107">Default (Default)</span></span>

```
Sort-Object [[-Property] <Object[]>] [-Descending] [-Unique] [-InputObject <psobject>]
 [-Culture <string>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="3232d-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3232d-108">DESCRIPTION</span></span>

<span data-ttu-id="3232d-109">此 `Sort-Object` Cmdlet 會根據物件屬性值，以遞增或遞減順序排序物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-109">The `Sort-Object` cmdlet sorts objects in ascending or descending order based on object property values.</span></span> <span data-ttu-id="3232d-110">如果命令中沒有包含排序屬性，PowerShell 會使用第一個輸入物件的預設排序屬性。</span><span class="sxs-lookup"><span data-stu-id="3232d-110">If sort properties are not included in a command, PowerShell uses default sort properties of the first input object.</span></span> <span data-ttu-id="3232d-111">如果輸入物件的類型沒有預設排序屬性，PowerShell 會嘗試比較物件本身。</span><span class="sxs-lookup"><span data-stu-id="3232d-111">If the type of the input object has no default sort properties, PowerShell attempts to compare the objects themselves.</span></span> <span data-ttu-id="3232d-112">如需詳細資訊，請參閱 [附注](#notes) 一節。</span><span class="sxs-lookup"><span data-stu-id="3232d-112">For more information, see the [Notes](#notes) section.</span></span>

<span data-ttu-id="3232d-113">您可以依單一屬性或多個屬性來排序物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-113">You can sort objects by a single property or multiple properties.</span></span> <span data-ttu-id="3232d-114">多個屬性會使用雜湊表，以遞增順序、遞減順序或排序次序的組合來排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-114">Multiple properties use hash tables to sort in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="3232d-115">屬性會排序為區分大小寫或不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3232d-115">Properties are sorted as case-sensitive or case-insensitive.</span></span> <span data-ttu-id="3232d-116">使用 **Unique** 參數可消除輸出中的重複專案。</span><span class="sxs-lookup"><span data-stu-id="3232d-116">Use the **Unique** parameter to eliminate duplicates from the output.</span></span>

## <span data-ttu-id="3232d-117">範例</span><span class="sxs-lookup"><span data-stu-id="3232d-117">EXAMPLES</span></span>

### <span data-ttu-id="3232d-118">範例 1︰依名稱排序目前的目錄</span><span class="sxs-lookup"><span data-stu-id="3232d-118">Example 1: Sort the current directory by name</span></span>

<span data-ttu-id="3232d-119">此命令會排序目錄中的檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="3232d-119">This command sorts the files and subdirectories in a directory.</span></span>

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

<span data-ttu-id="3232d-120">`Get-ChildItem`Cmdlet 會從 **Path** 參數 **C:\Test** 所指定的目錄中取得檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="3232d-120">The `Get-ChildItem` cmdlet gets the files and subdirectories from the directory specified by the **Path** parameter, **C:\Test** .</span></span> <span data-ttu-id="3232d-121">這些物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-121">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="3232d-122">`Sort-Object` 未指定屬性，因此輸出會依預設排序屬性 [ **名稱** ] 排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-122">`Sort-Object` does not specify a property so the output is sorted by the default sort property, **Name** .</span></span>

### <span data-ttu-id="3232d-123">範例 2︰依檔案長度排序目前的目錄</span><span class="sxs-lookup"><span data-stu-id="3232d-123">Example 2: Sort the current directory by file length</span></span>

<span data-ttu-id="3232d-124">此命令會依長度以遞增順序顯示目前目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="3232d-124">This command displays the files in the current directory by length in ascending order.</span></span>

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

<span data-ttu-id="3232d-125">`Get-ChildItem`Cmdlet 會從 **Path** 參數所指定的目錄取得檔案。</span><span class="sxs-lookup"><span data-stu-id="3232d-125">The `Get-ChildItem` cmdlet gets the files from the directory specified by the **Path** parameter.</span></span>
<span data-ttu-id="3232d-126">**File** 參數指定 `Get-ChildItem` 只取得檔案物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-126">The **File** parameter specifies that `Get-ChildItem` only gets file objects.</span></span> <span data-ttu-id="3232d-127">這些物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-127">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-128">`Sort-Object` 使用 **length** 參數，依長度以遞增順序排序檔案。</span><span class="sxs-lookup"><span data-stu-id="3232d-128">`Sort-Object` uses the **Length** parameter to sort the files by length in ascending order.</span></span>

### <span data-ttu-id="3232d-129">範例3：依記憶體使用量排序處理常式</span><span class="sxs-lookup"><span data-stu-id="3232d-129">Example 3: Sort processes by memory usage</span></span>

<span data-ttu-id="3232d-130">這個範例會根據 (WS) 大小的工作集，顯示記憶體使用量最高的進程。</span><span class="sxs-lookup"><span data-stu-id="3232d-130">This example displays processes with the highest memory usage based on their working set (WS) size.</span></span>

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

<span data-ttu-id="3232d-131">`Get-Process`Cmdlet 會取得在電腦上執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-131">The `Get-Process` cmdlet gets the list of processes running on the computer.</span></span> <span data-ttu-id="3232d-132">處理常式物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-132">The process objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-133">`Sort-Object` 使用 **Property** 參數來依 **WS** 排序物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-133">`Sort-Object` uses the **Property** parameter to sort the objects by **WS** .</span></span> <span data-ttu-id="3232d-134">這些物件會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-134">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="3232d-135">`Select-Object` 使用 **最後一個** 參數來指定最後五個物件，也就是具有最高 **WS** 使用量的物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-135">`Select-Object` uses the **Last** parameter to specify the last five objects, which are the objects with the highest **WS** usage.</span></span>

### <span data-ttu-id="3232d-136">範例4：依識別碼排序 HistoryInfo 物件</span><span class="sxs-lookup"><span data-stu-id="3232d-136">Example 4: Sort HistoryInfo objects by Id</span></span>

<span data-ttu-id="3232d-137">此命令會使用 **Id** 屬性來排序 PowerShell 會話的 **HistoryInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-137">This command sorts the PowerShell session's **HistoryInfo** objects using the **Id** property.</span></span> <span data-ttu-id="3232d-138">每個 PowerShell 會話都有自己的命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="3232d-138">Each PowerShell session has its own command history.</span></span>

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

<span data-ttu-id="3232d-139">`Get-History`Cmdlet 會從目前的 PowerShell 會話取得歷程記錄物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-139">The `Get-History` cmdlet gets the history objects from the current PowerShell session.</span></span> <span data-ttu-id="3232d-140">這些物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-140">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-141">`Sort-Object` 使用 **Property** 參數依 **識別碼** 排序物件。 **遞減** 參數會將命令歷程記錄從最新排序到最舊。</span><span class="sxs-lookup"><span data-stu-id="3232d-141">`Sort-Object` uses the **Property** parameter to sort the objects by **Id** . The **Descending** parameter sorts the command history from newest to oldest.</span></span>

### <span data-ttu-id="3232d-142">範例5：使用雜湊表以遞增和遞減順序排序屬性</span><span class="sxs-lookup"><span data-stu-id="3232d-142">Example 5: Use a hash table to sort properties in ascending and descending order</span></span>

<span data-ttu-id="3232d-143">此命令會使用兩個屬性來排序物件、 **狀態** 和 **DisplayName** 。</span><span class="sxs-lookup"><span data-stu-id="3232d-143">This command uses two properties to sort the objects, **Status** and **DisplayName** .</span></span> <span data-ttu-id="3232d-144">**狀態** 會以遞減順序排序，而 **DisplayName** 會以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-144">**Status** is sorted in descending order and **DisplayName** is sorted in ascending order.</span></span>

<span data-ttu-id="3232d-145">雜湊表可用來指定 **屬性** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="3232d-145">A hash table is used to specify the **Property** parameter's value.</span></span> <span data-ttu-id="3232d-146">雜湊表會使用運算式來指定屬性名稱和排序次序。</span><span class="sxs-lookup"><span data-stu-id="3232d-146">The hash table uses an expression to specify the property names and sort orders.</span></span> <span data-ttu-id="3232d-147">如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="3232d-147">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="3232d-148">雜湊表中使用的 **Status** 屬性是列舉屬性。</span><span class="sxs-lookup"><span data-stu-id="3232d-148">The **Status** property used in the hash table is an enumerated property.</span></span>
<span data-ttu-id="3232d-149">如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。</span><span class="sxs-lookup"><span data-stu-id="3232d-149">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

<span data-ttu-id="3232d-150">`Get-Service`Cmdlet 會取得電腦上的服務清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-150">The `Get-Service` cmdlet gets the list of services on the computer.</span></span> <span data-ttu-id="3232d-151">服務物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-151">The service objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-152">`Sort-Object` 使用 **property** 參數搭配雜湊表來指定屬性名稱和排序次序。</span><span class="sxs-lookup"><span data-stu-id="3232d-152">`Sort-Object` uses the **Property** parameter with a hash table to specify the property names and sort orders.</span></span> <span data-ttu-id="3232d-153">**屬性** 參數會依兩個屬性 **排序，以** 遞減順序和 **DisplayName** 以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-153">The **Property** parameter is sorted by two properties, **Status** in descending order and **DisplayName** in ascending order.</span></span>

<span data-ttu-id="3232d-154">**狀態** 是列舉的屬性。</span><span class="sxs-lookup"><span data-stu-id="3232d-154">**Status** is an enumerated property.</span></span> <span data-ttu-id="3232d-155">[已 **停止** ] 的值為 **1** **，且執行的值** 為 **4** 。</span><span class="sxs-lookup"><span data-stu-id="3232d-155">**Stopped** has a value of **1** and **Running** has a value of **4** .</span></span> <span data-ttu-id="3232d-156">**遞減** 的參數會設定為， `$True` 以便 **Running** 在 **停止** 的進程之前顯示執行中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="3232d-156">The **Descending** parameter is set to `$True` so that **Running** processes are displayed before **Stopped** processes.</span></span> <span data-ttu-id="3232d-157">**DisplayName** 會將 **遞減** 參數設定為， `$False` 以依字母順序排序顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3232d-157">**DisplayName** sets the **Descending** parameter to `$False` to sort the display names in alphabetical order.</span></span>

### <span data-ttu-id="3232d-158">範例 6︰依時間範圍排序文字檔案</span><span class="sxs-lookup"><span data-stu-id="3232d-158">Example 6: Sort text files by time span</span></span>

<span data-ttu-id="3232d-159">此命令會依 **CreationTime** 和 **LastWriteTime** 之間的時間範圍，以遞減順序排序文字檔。</span><span class="sxs-lookup"><span data-stu-id="3232d-159">This command sorts text files in descending order by the time span between **CreationTime** and **LastWriteTime** .</span></span>

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt

```

<span data-ttu-id="3232d-160">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 **C:\Test** 和所有檔案 `*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="3232d-160">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** and all of the `*.txt` files.</span></span> <span data-ttu-id="3232d-161">這些物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-161">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="3232d-162">`Sort-Object` 使用 **Property** 參數搭配雜湊表，以判斷每個檔案在 **CreationTime** 和 **LastWriteTime** 之間的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="3232d-162">`Sort-Object` uses the **Property** parameter with a hash table to determine each files time span between **CreationTime** and **LastWriteTime** .</span></span> <span data-ttu-id="3232d-163">**遞減** 的參數會設定為， `$False` 以最長到最短時間範圍的順序排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-163">The **Descending** parameter is set to `$False` to sort in the order of longest to shortest time span.</span></span>

### <span data-ttu-id="3232d-164">範例 7︰在文字檔案中排序名稱</span><span class="sxs-lookup"><span data-stu-id="3232d-164">Example 7: Sort names in a text file</span></span>

<span data-ttu-id="3232d-165">此範例顯示如何從文字檔排序清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-165">This example shows how to sort a list from a text file.</span></span> <span data-ttu-id="3232d-166">原始檔案會顯示為未排序的清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-166">The original file is displayed as an unsorted list.</span></span> <span data-ttu-id="3232d-167">`Sort-Object` 排序內容，然後使用移除重複專案的 **唯一** 參數來排序內容。</span><span class="sxs-lookup"><span data-stu-id="3232d-167">`Sort-Object` sorts the contents and then sorts the contents with the **Unique** parameter that removes duplicates.</span></span>

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

<span data-ttu-id="3232d-168">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。</span><span class="sxs-lookup"><span data-stu-id="3232d-168">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="3232d-169">File **ServerNames.txt** 包含未排序的電腦名稱稱清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-169">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span>

<span data-ttu-id="3232d-170">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。</span><span class="sxs-lookup"><span data-stu-id="3232d-170">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="3232d-171">File **ServerNames.txt** 包含未排序的電腦名稱稱清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-171">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="3232d-172">這些物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-172">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-173">`Sort-Object` 以預設順序昇冪排序清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-173">`Sort-Object` sorts the list in the default order, ascending.</span></span>

<span data-ttu-id="3232d-174">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。</span><span class="sxs-lookup"><span data-stu-id="3232d-174">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="3232d-175">File **ServerNames.txt** 包含未排序的電腦名稱稱清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-175">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="3232d-176">這些物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-176">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-177">`Sort-Object` 使用 **Unique** 參數移除重複的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="3232d-177">`Sort-Object` uses the **Unique** parameter to remove duplicate computer names.</span></span> <span data-ttu-id="3232d-178">清單會以預設順序（遞增）排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-178">The list is sorted in the default order, ascending.</span></span>

### <span data-ttu-id="3232d-179">範例8：將字串排序為整數</span><span class="sxs-lookup"><span data-stu-id="3232d-179">Example 8: Sort a string as an integer</span></span>

<span data-ttu-id="3232d-180">這個範例示範如何將包含字串物件的文字檔排序為整數。</span><span class="sxs-lookup"><span data-stu-id="3232d-180">This example shows how to sort a text file that contains string objects as integers.</span></span> <span data-ttu-id="3232d-181">您可以將管線中的每個命令向下傳送至 `Get-Member` ，並確認物件是字串，而不是整數。</span><span class="sxs-lookup"><span data-stu-id="3232d-181">You can send each command down the pipeline to `Get-Member` and verify that the objects are strings instead of integers.</span></span> <span data-ttu-id="3232d-182">在這些範例中，檔案 `ProductId.txt` 包含未排序的產品編號清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-182">For these examples, the `ProductId.txt` file contains an unsorted list of product numbers.</span></span>

<span data-ttu-id="3232d-183">在第一個範例中，會取得檔案的 `Get-Content` 內容以及 Cmdlet 的管道線 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3232d-183">In the first example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-184">`Sort-Object` 以遞增順序排序字串物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-184">`Sort-Object` sorts the string objects in ascending order.</span></span>

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

<span data-ttu-id="3232d-185">在第二個範例中，會取得檔案的 `Get-Content` 內容以及 Cmdlet 的管道線 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3232d-185">In the second example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-186">`Sort-Object` 使用腳本區塊將字串轉換成整數。</span><span class="sxs-lookup"><span data-stu-id="3232d-186">`Sort-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="3232d-187">在範例程式碼中， `[int]` 會將字串轉換成整數，並 `$_` 代表每個字串，因為它會在管線中關閉。</span><span class="sxs-lookup"><span data-stu-id="3232d-187">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="3232d-188">整數物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-188">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="3232d-189">`Sort-Object` 依數位順序排序整數物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-189">`Sort-Object` sorts the integer objects in numeric order.</span></span>

<span data-ttu-id="3232d-190">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定目錄和檔案名。</span><span class="sxs-lookup"><span data-stu-id="3232d-190">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="3232d-191">檔案 **ProductId.txt** 包含未排序的產品編號清單。</span><span class="sxs-lookup"><span data-stu-id="3232d-191">The file **ProductId.txt** contains an unsorted list of product numbers.</span></span> <span data-ttu-id="3232d-192">字串物件會將管線向下傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-192">The string objects are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="3232d-193">`ForEach-Object` 使用腳本區塊將字串轉換成整數。</span><span class="sxs-lookup"><span data-stu-id="3232d-193">`ForEach-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="3232d-194">在範例程式碼中， `[int]` 會將字串轉換成整數，並 `$_` 代表每個字串，因為它會在管線中關閉。</span><span class="sxs-lookup"><span data-stu-id="3232d-194">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="3232d-195">整數物件會向下傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3232d-195">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="3232d-196">`Sort-Object` 依數位順序排序整數物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-196">`Sort-Object` sorts the integer objects in numeric order.</span></span>
## <span data-ttu-id="3232d-197">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3232d-197">PARAMETERS</span></span>

### <span data-ttu-id="3232d-198">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="3232d-198">-CaseSensitive</span></span>

<span data-ttu-id="3232d-199">指出排序會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3232d-199">Indicates that the sort is case-sensitive.</span></span> <span data-ttu-id="3232d-200">依預設，排序不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3232d-200">By default, sorts are not case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3232d-201">-Culture</span><span class="sxs-lookup"><span data-stu-id="3232d-201">-Culture</span></span>

<span data-ttu-id="3232d-202">指定要用於排序的文化設定。</span><span class="sxs-lookup"><span data-stu-id="3232d-202">Specifies the cultural configuration to use for sorts.</span></span> <span data-ttu-id="3232d-203">使用 `Get-Culture` 來顯示系統的文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="3232d-203">Use `Get-Culture` to display the system's culture configuration.</span></span>

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

### <span data-ttu-id="3232d-204">-Descending</span><span class="sxs-lookup"><span data-stu-id="3232d-204">-Descending</span></span>

<span data-ttu-id="3232d-205">表示 `Sort-Object` 以遞減順序排序物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-205">Indicates that `Sort-Object` sorts the objects in descending order.</span></span> <span data-ttu-id="3232d-206">預設值為遞增排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-206">The default is ascending order.</span></span>

<span data-ttu-id="3232d-207">若要使用不同的排序次序來排序多個屬性，請使用雜湊表。</span><span class="sxs-lookup"><span data-stu-id="3232d-207">To sort multiple properties with different sort orders, use a hash table.</span></span> <span data-ttu-id="3232d-208">例如，您可以使用雜湊表，以遞增順序排序一個屬性，並以遞減順序排序另一個屬性。</span><span class="sxs-lookup"><span data-stu-id="3232d-208">For example, with a hash table you can sort one property in ascending order and another property in descending order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3232d-209">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3232d-209">-InputObject</span></span>

<span data-ttu-id="3232d-210">若要排序物件，請將其傳送至管線 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3232d-210">To sort objects, send them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="3232d-211">如果您使用 **InputObject** 參數來提交專案的集合，則 `Sort-Object` 會接收代表集合的一個物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-211">If you use the **InputObject** parameter to submit a collection of items, `Sort-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="3232d-212">因為無法排序一個物件，所以會傳回 `Sort-Object` 未變更的整個集合。</span><span class="sxs-lookup"><span data-stu-id="3232d-212">Because one object cannot be sorted, `Sort-Object` returns the entire collection unchanged.</span></span>

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

### <span data-ttu-id="3232d-213">-Property</span><span class="sxs-lookup"><span data-stu-id="3232d-213">-Property</span></span>

<span data-ttu-id="3232d-214">指定 `Sort-Object` 用來排序物件的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3232d-214">Specifies the property names that `Sort-Object` uses to sort the objects.</span></span> <span data-ttu-id="3232d-215">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3232d-215">Wildcards are permitted.</span></span>
<span data-ttu-id="3232d-216">物件會根據屬性值排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-216">Objects are sorted based on the property values.</span></span> <span data-ttu-id="3232d-217">如果您未指定屬性，則會 `Sort-Object` 根據物件類型或物件本身的預設屬性進行排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-217">If you do not specify a property, `Sort-Object` sorts based on default properties for the object type or the objects themselves.</span></span>

<span data-ttu-id="3232d-218">您可以依遞增順序、遞減順序或排序次序的組合來排序多個屬性。</span><span class="sxs-lookup"><span data-stu-id="3232d-218">Multiple properties can be sorted in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="3232d-219">當您指定多個屬性時，物件會依第一個屬性排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-219">When you specify multiple properties, the objects are sorted by the first property.</span></span> <span data-ttu-id="3232d-220">如果有多個物件的第一個屬性具有相同的值，則會依第二個屬性排序這些物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-220">If multiple objects have the same value for the first property, those objects are sorted by the second property.</span></span> <span data-ttu-id="3232d-221">此程序會持續執行到沒有指定的屬性或物件群組為止。</span><span class="sxs-lookup"><span data-stu-id="3232d-221">This process continues until there are no more specified properties or no groups of objects.</span></span>

<span data-ttu-id="3232d-222">**屬性** 參數的值可以是計算的屬性。</span><span class="sxs-lookup"><span data-stu-id="3232d-222">The **Property** parameter's value can be a calculated property.</span></span> <span data-ttu-id="3232d-223">若要建立計算的屬性，請使用雜湊表。</span><span class="sxs-lookup"><span data-stu-id="3232d-223">To create a calculated property, use a hash table.</span></span>

<span data-ttu-id="3232d-224">雜湊表的有效索引鍵如下所示：</span><span class="sxs-lookup"><span data-stu-id="3232d-224">Valid keys for a hash table are as follows:</span></span>

- <span data-ttu-id="3232d-225">`expression` - `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="3232d-225">`expression` - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="3232d-226">`ascending` 或 `descending` - `<boolean>`</span><span class="sxs-lookup"><span data-stu-id="3232d-226">`ascending` or `descending` - `<boolean>`</span></span>

<span data-ttu-id="3232d-227">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3232d-227">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3232d-228">-Unique</span><span class="sxs-lookup"><span data-stu-id="3232d-228">-Unique</span></span>

<span data-ttu-id="3232d-229">指出會 `Sort-Object` 排除重複專案，並只傳回集合的唯一成員。</span><span class="sxs-lookup"><span data-stu-id="3232d-229">Indicates that `Sort-Object` eliminates duplicates and returns only the unique members of the collection.</span></span> <span data-ttu-id="3232d-230">唯一值的第一個實例會包含在排序的輸出中。</span><span class="sxs-lookup"><span data-stu-id="3232d-230">The first instance of a unique value is included in the sorted output.</span></span>

<span data-ttu-id="3232d-231">**Unique** 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3232d-231">**Unique** is case-insensitive.</span></span> <span data-ttu-id="3232d-232">只有字元大小寫不同的字串會被視為相同。</span><span class="sxs-lookup"><span data-stu-id="3232d-232">Strings that only differ by character case are considered the same.</span></span>
<span data-ttu-id="3232d-233">例如，字元和字元。</span><span class="sxs-lookup"><span data-stu-id="3232d-233">For example, character and CHARACTER.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3232d-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3232d-234">CommonParameters</span></span>

<span data-ttu-id="3232d-235">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3232d-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3232d-236">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3232d-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3232d-237">輸入</span><span class="sxs-lookup"><span data-stu-id="3232d-237">INPUTS</span></span>

### <span data-ttu-id="3232d-238">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="3232d-238">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3232d-239">您可以透過管線傳送要排序的物件 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3232d-239">You can pipe the objects to be sorted to `Sort-Object`.</span></span>

## <span data-ttu-id="3232d-240">輸出</span><span class="sxs-lookup"><span data-stu-id="3232d-240">OUTPUTS</span></span>

### <span data-ttu-id="3232d-241">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="3232d-241">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3232d-242">`Sort-Object` 傳回已排序的物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-242">`Sort-Object` returns the sorted objects.</span></span>

## <span data-ttu-id="3232d-243">注意</span><span class="sxs-lookup"><span data-stu-id="3232d-243">NOTES</span></span>

<span data-ttu-id="3232d-244">此 `Sort-Object` Cmdlet 會根據命令中指定的屬性或物件類型的預設排序屬性來排序物件。</span><span class="sxs-lookup"><span data-stu-id="3232d-244">The `Sort-Object` cmdlet sorts objects based on properties specified in the command or the default sort properties for the object type.</span></span> <span data-ttu-id="3232d-245">預設排序屬性是使用在檔案 `PropertySet` 中命名的來定義 `DefaultKeyPropertySet` `types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="3232d-245">Default sort properties are defined using the `PropertySet` named `DefaultKeyPropertySet` in a `types.ps1xml` file.</span></span> <span data-ttu-id="3232d-246">如需詳細資訊，請參閱 [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="3232d-246">For more information, see [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span></span>

<span data-ttu-id="3232d-247">如果物件沒有其中一個指定的屬性，則會將該物件的屬性值解釋 `Sort-Object` 為 **Null** ，並置於排序次序的結尾。</span><span class="sxs-lookup"><span data-stu-id="3232d-247">If an object does not have one of the specified properties, the property value for that object is interpreted by `Sort-Object` as **Null** and placed at the end of the sort order.</span></span>

<span data-ttu-id="3232d-248">當沒有排序屬性可用時，PowerShell 會嘗試比較物件本身。</span><span class="sxs-lookup"><span data-stu-id="3232d-248">When no sort properties are available, PowerShell attempts to compare the objects themselves.</span></span>
<span data-ttu-id="3232d-249">`Sort-Object` 針對每個屬性使用 **Compare** 方法。</span><span class="sxs-lookup"><span data-stu-id="3232d-249">`Sort-Object` uses the **Compare** method for each property.</span></span> <span data-ttu-id="3232d-250">如果屬性不會執行 **IComparable** ，此 Cmdlet 會將屬性值轉換為字串，並針對 **system.string** 使用 **Compare** 方法。</span><span class="sxs-lookup"><span data-stu-id="3232d-250">If a property does not implement **IComparable** , the cmdlet converts the property value to a string and uses the **Compare** method for **System.String** .</span></span> <span data-ttu-id="3232d-251">如需詳細資訊，請參閱 [CompareTo (物件) 方法](/dotnet/api/system.management.automation.psobject.compareto)。</span><span class="sxs-lookup"><span data-stu-id="3232d-251">For more information, see [PSObject.CompareTo(Object) Method](/dotnet/api/system.management.automation.psobject.compareto).</span></span>

<span data-ttu-id="3232d-252">如果您對列舉屬性（例如 **狀態** ）進行排序，則 `Sort-Object` 依列舉值排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-252">If you sort on an enumerated property such as **Status** , `Sort-Object` sorts by the enumeration values.</span></span> <span data-ttu-id="3232d-253">針對 Windows 服務，已 **停止** 的值為 **1** ， **且執行的值** 為 **4** 。</span><span class="sxs-lookup"><span data-stu-id="3232d-253">For Windows services, **Stopped** has a value of **1** and **Running** has a value of **4** .</span></span>
<span data-ttu-id="3232d-254">**由於列舉** 值的原因，已 **停止** 會先排序。</span><span class="sxs-lookup"><span data-stu-id="3232d-254">**Stopped** is sorted before **Running** because of the enumerated values.</span></span> <span data-ttu-id="3232d-255">如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。</span><span class="sxs-lookup"><span data-stu-id="3232d-255">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="3232d-256">相關連結</span><span class="sxs-lookup"><span data-stu-id="3232d-256">RELATED LINKS</span></span>

[<span data-ttu-id="3232d-257">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="3232d-257">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="3232d-258">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="3232d-258">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="3232d-259">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3232d-259">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="3232d-260">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-260">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="3232d-261">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-261">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="3232d-262">Group-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-262">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="3232d-263">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-263">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="3232d-264">New-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-264">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="3232d-265">Select-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-265">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="3232d-266">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="3232d-266">Tee-Object</span></span>](Tee-Object.md)
