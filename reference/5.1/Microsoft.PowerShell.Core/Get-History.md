---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: ae9cc8b0daf9a3c25d4385fbca156e8a146334da
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "93206364"
---
# <span data-ttu-id="c8226-103">Get-History</span><span class="sxs-lookup"><span data-stu-id="c8226-103">Get-History</span></span>

## <span data-ttu-id="c8226-104">概要</span><span class="sxs-lookup"><span data-stu-id="c8226-104">SYNOPSIS</span></span>
<span data-ttu-id="c8226-105">取得目前工作階段期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="c8226-105">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="c8226-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8226-106">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="c8226-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c8226-107">DESCRIPTION</span></span>

<span data-ttu-id="c8226-108">此 `Get-History` Cmdlet 會取得會話歷程記錄，也就是在目前會話期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="c8226-108">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="c8226-109">PowerShell 會自動維護每個會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="c8226-109">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="c8226-110">會話歷程記錄中的專案數取決於喜好設定變數的值 `$MaximumHistoryCount` 。</span><span class="sxs-lookup"><span data-stu-id="c8226-110">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="c8226-111">從 Windows PowerShell 3.0 開始，預設值為 `4096` 。</span><span class="sxs-lookup"><span data-stu-id="c8226-111">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="c8226-112">根據預設，歷程記錄檔案會儲存在主目錄中，但是您可以將檔案儲存在任何位置。</span><span class="sxs-lookup"><span data-stu-id="c8226-112">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="c8226-113">如需 PowerShell 中歷程記錄功能的詳細資訊，請參閱 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="c8226-113">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="c8226-114">會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。</span><span class="sxs-lookup"><span data-stu-id="c8226-114">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="c8226-115">這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="c8226-115">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="c8226-116">此 Cmdlet 僅適用于會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="c8226-116">This cmdlet only works with the session history.</span></span> <span data-ttu-id="c8226-117">如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="c8226-117">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="c8226-118">範例</span><span class="sxs-lookup"><span data-stu-id="c8226-118">EXAMPLES</span></span>

### <span data-ttu-id="c8226-119">範例1：取得會話歷程記錄</span><span class="sxs-lookup"><span data-stu-id="c8226-119">Example 1: Get the session history</span></span>

<span data-ttu-id="c8226-120">這個範例會取得會話歷程記錄中的專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-120">This example gets the entries in the session history.</span></span> <span data-ttu-id="c8226-121">預設顯示會顯示每個命令和它的識別碼，指出它們的執行順序。</span><span class="sxs-lookup"><span data-stu-id="c8226-121">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="c8226-122">範例2：取得包含字串的專案</span><span class="sxs-lookup"><span data-stu-id="c8226-122">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="c8226-123">此範例會取得命令歷程記錄中包含字串服務的專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-123">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="c8226-124">第一個命令會取得工作階段歷程記錄中所有項目。</span><span class="sxs-lookup"><span data-stu-id="c8226-124">The first command gets all entries in the session history.</span></span> <span data-ttu-id="c8226-125">管線運算子 () 會將 `|` 結果傳遞至 `Where-Object` Cmdlet，此 Cmdlet 只會選取包含服務的命令。</span><span class="sxs-lookup"><span data-stu-id="c8226-125">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="c8226-126">範例3：將記錄專案匯出至特定識別碼</span><span class="sxs-lookup"><span data-stu-id="c8226-126">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="c8226-127">這個範例會取得以專案7結尾的五個最新歷程記錄專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-127">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="c8226-128">管線運算子會將結果傳遞至 `Export-Csv` Cmdlet，此 Cmdlet 會將歷程記錄格式化為逗點分隔的文字，並將其儲存在 History.csv 檔案中。</span><span class="sxs-lookup"><span data-stu-id="c8226-128">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="c8226-129">檔案包含將歷程記錄格式化為清單時所顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="c8226-129">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="c8226-130">這包括命令的狀態和開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="c8226-130">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="c8226-131">範例4：顯示最新的命令</span><span class="sxs-lookup"><span data-stu-id="c8226-131">Example 4: Display the most recent command</span></span>

<span data-ttu-id="c8226-132">此範例會取得命令歷程記錄中的最後一個命令。</span><span class="sxs-lookup"><span data-stu-id="c8226-132">This example gets the last command in the command history.</span></span> <span data-ttu-id="c8226-133">最後一個命令是最近輸入的命令。</span><span class="sxs-lookup"><span data-stu-id="c8226-133">The last command is the most recently entered command.</span></span> <span data-ttu-id="c8226-134">此命令會使用 **Count** 參數只顯示一個命令。</span><span class="sxs-lookup"><span data-stu-id="c8226-134">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="c8226-135">根據預設，會 `Get-History` 取得最新的命令。</span><span class="sxs-lookup"><span data-stu-id="c8226-135">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="c8226-136">此命令可以縮寫成 "h -c 1"，而且相當於按下向上鍵。</span><span class="sxs-lookup"><span data-stu-id="c8226-136">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="c8226-137">範例5：顯示歷程記錄中所有專案的屬性</span><span class="sxs-lookup"><span data-stu-id="c8226-137">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="c8226-138">此範例會顯示會話歷程記錄中所有專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="c8226-138">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="c8226-139">管線運算子會將命令的結果傳遞 `Get-History` 給 `Format-List` Cmdlet，以顯示每個歷程記錄專案的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="c8226-139">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="c8226-140">這包括命令的識別碼、狀態和開始與結束時間。</span><span class="sxs-lookup"><span data-stu-id="c8226-140">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="c8226-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c8226-141">PARAMETERS</span></span>

### <span data-ttu-id="c8226-142">-Count</span><span class="sxs-lookup"><span data-stu-id="c8226-142">-Count</span></span>

<span data-ttu-id="c8226-143">指定此 Cmdlet 取得的最新歷程記錄專案數目。</span><span class="sxs-lookup"><span data-stu-id="c8226-143">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="c8226-144">依預設，會 `Get-History` 取得會話歷程記錄中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-144">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="c8226-145">如果您同時在命令中使用 **Count** 和 **Id** 參數，畫面結尾會是 **Id** 參數所指定的命令。</span><span class="sxs-lookup"><span data-stu-id="c8226-145">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="c8226-146">在 Windows PowerShell 2.0 中，預設會 `Get-History` 取得32的最新專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-146">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c8226-147">-Id</span><span class="sxs-lookup"><span data-stu-id="c8226-147">-Id</span></span>

<span data-ttu-id="c8226-148">指定會話歷程記錄中專案的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="c8226-148">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="c8226-149">`Get-History` 只取得指定的專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-149">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="c8226-150">如果您在命令中同時使用 **id** 和 **Count** 參數，會 `Get-History` 取得以 **id** 參數指定的專案結尾的最新專案。</span><span class="sxs-lookup"><span data-stu-id="c8226-150">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c8226-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8226-151">CommonParameters</span></span>

<span data-ttu-id="c8226-152">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c8226-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8226-153">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c8226-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8226-154">輸入</span><span class="sxs-lookup"><span data-stu-id="c8226-154">INPUTS</span></span>

### <span data-ttu-id="c8226-155">System.Int64</span><span class="sxs-lookup"><span data-stu-id="c8226-155">System.Int64</span></span>

<span data-ttu-id="c8226-156">您可以使用管線將歷程記錄識別碼傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8226-156">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="c8226-157">輸出</span><span class="sxs-lookup"><span data-stu-id="c8226-157">OUTPUTS</span></span>

### <span data-ttu-id="c8226-158">Microsoft.PowerShell.Commands.HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="c8226-158">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="c8226-159">這個 Cmdlet 會針對它取得的每個歷程記錄專案傳回一個歷程記錄物件。</span><span class="sxs-lookup"><span data-stu-id="c8226-159">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="c8226-160">注意</span><span class="sxs-lookup"><span data-stu-id="c8226-160">NOTES</span></span>

<span data-ttu-id="c8226-161">工作階段歷程記錄是工作階段期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="c8226-161">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="c8226-162">會話歷程記錄代表命令的執行順序、狀態，以及開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="c8226-162">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="c8226-163">當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="c8226-163">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="c8226-164">如需命令歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="c8226-164">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="c8226-165">從 Windows PowerShell 3.0 開始，喜好設定變數的預設值 `$MaximumHistoryCount` 為 `4096` 。</span><span class="sxs-lookup"><span data-stu-id="c8226-165">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="c8226-166">在 Windows PowerShell 2.0 中，預設值為 `64` 。</span><span class="sxs-lookup"><span data-stu-id="c8226-166">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="c8226-167">如需變數的詳細資訊 `$MaximumHistoryCount` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c8226-167">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="c8226-168">相關連結</span><span class="sxs-lookup"><span data-stu-id="c8226-168">RELATED LINKS</span></span>

[<span data-ttu-id="c8226-169">Add-History</span><span class="sxs-lookup"><span data-stu-id="c8226-169">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="c8226-170">Clear-History</span><span class="sxs-lookup"><span data-stu-id="c8226-170">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="c8226-171">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="c8226-171">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="c8226-172">about_History</span><span class="sxs-lookup"><span data-stu-id="c8226-172">about_History</span></span>](About/about_History.md)
