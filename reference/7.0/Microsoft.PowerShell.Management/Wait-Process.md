---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 07986e4c7e8ead25e99ffc67ff8f9ffa2241af9b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201156"
---
# <span data-ttu-id="d62b2-103">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-103">Wait-Process</span></span>

## <span data-ttu-id="d62b2-104">概要</span><span class="sxs-lookup"><span data-stu-id="d62b2-104">SYNOPSIS</span></span>
<span data-ttu-id="d62b2-105">等候處理程序停止之後，才接受其他輸入。</span><span class="sxs-lookup"><span data-stu-id="d62b2-105">Waits for the processes to be stopped before accepting more input.</span></span>

## <span data-ttu-id="d62b2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d62b2-106">SYNTAX</span></span>

### <span data-ttu-id="d62b2-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="d62b2-107">Name (Default)</span></span>

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="d62b2-108">Id</span><span class="sxs-lookup"><span data-stu-id="d62b2-108">Id</span></span>

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="d62b2-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="d62b2-109">InputObject</span></span>

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## <span data-ttu-id="d62b2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d62b2-110">DESCRIPTION</span></span>

<span data-ttu-id="d62b2-111">**Wait-Process** Cmdlet 會等候一或多個正在執行的處理程序停止之後，才會接受輸入。</span><span class="sxs-lookup"><span data-stu-id="d62b2-111">The **Wait-Process** cmdlet waits for one or more running processes to be stopped before accepting input.</span></span>
<span data-ttu-id="d62b2-112">在 PowerShell 主控台中，這個 Cmdlet 會抑制命令提示字元，直到處理程式停止為止。</span><span class="sxs-lookup"><span data-stu-id="d62b2-112">In the PowerShell console, this cmdlet suppresses the command prompt until the processes are stopped.</span></span>
<span data-ttu-id="d62b2-113">您可以依處理程序名稱或處理程序識別碼 (PID) 來指定處理程序，或使用管道將處理程序物件傳送至 **Wait-Process** 。</span><span class="sxs-lookup"><span data-stu-id="d62b2-113">You can specify a process by process name or process ID (PID), or pipe a process object to **Wait-Process** .</span></span>

<span data-ttu-id="d62b2-114">**Wait-Process** 只適用於正在本機電腦上執行的處理程序。</span><span class="sxs-lookup"><span data-stu-id="d62b2-114">**Wait-Process** works only on processes running on the local computer.</span></span>

## <span data-ttu-id="d62b2-115">範例</span><span class="sxs-lookup"><span data-stu-id="d62b2-115">EXAMPLES</span></span>

### <span data-ttu-id="d62b2-116">範例 1︰停止處理程序並等候</span><span class="sxs-lookup"><span data-stu-id="d62b2-116">Example 1: Stop a process and wait</span></span>

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

<span data-ttu-id="d62b2-117">此範例會停止「記事本」處理程序，然後等候該處理程序停止之後，才繼續進行下一個命令。</span><span class="sxs-lookup"><span data-stu-id="d62b2-117">This example stops the Notepad process and then waits for the process to be stopped before it continues with the next command.</span></span>

<span data-ttu-id="d62b2-118">第一個命令會使用 **Get-Process** Cmdlet，來取得「記事本」處理程序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62b2-118">The first command uses the **Get-Process** cmdlet to get the ID of the Notepad process.</span></span>
<span data-ttu-id="d62b2-119">它會將識別碼儲存於 $nid 變數中。</span><span class="sxs-lookup"><span data-stu-id="d62b2-119">It stores the ID in the $nid variable.</span></span>

<span data-ttu-id="d62b2-120">第二個命令會使用 Stop-Process Cmdlet，來停止識別碼儲存於 $nid 中的處理程序。</span><span class="sxs-lookup"><span data-stu-id="d62b2-120">The second command uses the Stop-Process cmdlet to stop the process with the ID stored in $nid.</span></span>

<span data-ttu-id="d62b2-121">第三個命令會使用 **Wait-Process** 來等候，直到「記事本」處理程序停止為止。</span><span class="sxs-lookup"><span data-stu-id="d62b2-121">The third command uses **Wait-Process** to wait until the Notepad process is stopped.</span></span>
<span data-ttu-id="d62b2-122">它會使用 **Wait-Process** 的 *Id* 參數來識別處理程序。</span><span class="sxs-lookup"><span data-stu-id="d62b2-122">It uses the *Id* parameter of **Wait-Process** to identify the process.</span></span>

### <span data-ttu-id="d62b2-123">範例 2︰指定處理程序</span><span class="sxs-lookup"><span data-stu-id="d62b2-123">Example 2: Specifying a process</span></span>

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

<span data-ttu-id="d62b2-124">這些命令示範三種將處理程序指定給 **Wait-Process** 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="d62b2-124">These commands show three different methods of specifying a process to **Wait-Process** .</span></span>
<span data-ttu-id="d62b2-125">第一個命令會取得「記事本」處理程序，並將它儲存於 $p 變數中。</span><span class="sxs-lookup"><span data-stu-id="d62b2-125">The first command gets the Notepad process and stores it in the $p variable.</span></span>

<span data-ttu-id="d62b2-126">第二個命令會使用 *Id* 參數、第三個命令會使用 *Name* 參數，而第四個命令會使用 *InputObject* 參數。</span><span class="sxs-lookup"><span data-stu-id="d62b2-126">The second command uses the *Id* parameter, the third command uses the *Name* parameter, and the fourth command uses the *InputObject* parameter.</span></span>

<span data-ttu-id="d62b2-127">這些命令的結果皆相同，並且可交換使用。</span><span class="sxs-lookup"><span data-stu-id="d62b2-127">These commands have the same results and can be used interchangeably.</span></span>

### <span data-ttu-id="d62b2-128">範例 3︰等候處理程序一段指定的時間</span><span class="sxs-lookup"><span data-stu-id="d62b2-128">Example 3: Wait for processes for a specified time</span></span>

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

<span data-ttu-id="d62b2-129">這個命令會等候 30 秒讓 Outlook 和 Winword 處理程序停止。</span><span class="sxs-lookup"><span data-stu-id="d62b2-129">This command waits 30 seconds for the Outlook and Winword processes to stop.</span></span>
<span data-ttu-id="d62b2-130">如果這兩個處理程序都沒有停止，則此 Cmdlet 會顯示一個非終止錯誤和命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d62b2-130">If both processes are not stopped, the cmdlet displays a non-terminating error and the command prompt.</span></span>

## <span data-ttu-id="d62b2-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d62b2-131">PARAMETERS</span></span>

### <span data-ttu-id="d62b2-132">-Id</span><span class="sxs-lookup"><span data-stu-id="d62b2-132">-Id</span></span>

<span data-ttu-id="d62b2-133">指定處理程序的處理程序識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62b2-133">Specifies the process IDs of the processes.</span></span>
<span data-ttu-id="d62b2-134">若要指定多個識別碼，請使用逗號來分隔識別碼。</span><span class="sxs-lookup"><span data-stu-id="d62b2-134">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="d62b2-135">若要尋找處理程序的 PID，請輸入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="d62b2-135">To find the PID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d62b2-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d62b2-136">-InputObject</span></span>

<span data-ttu-id="d62b2-137">藉由送出處理程序物件來指定處理程序。</span><span class="sxs-lookup"><span data-stu-id="d62b2-137">Specifies the processes by submitting process objects.</span></span>
<span data-ttu-id="d62b2-138">輸入包含處理程序物件的變數，或輸入可取得處理程序物件的命令或運算式，例如 Get-Process Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d62b2-138">Enter a variable that contains the process objects, or type a command or expression that gets the process objects, such as the Get-Process cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d62b2-139">-Name</span><span class="sxs-lookup"><span data-stu-id="d62b2-139">-Name</span></span>

<span data-ttu-id="d62b2-140">指定處理程序的處理程序名稱。</span><span class="sxs-lookup"><span data-stu-id="d62b2-140">Specifies the process names of the processes.</span></span>
<span data-ttu-id="d62b2-141">若要指定多個名稱，請使用逗號來分隔名稱。</span><span class="sxs-lookup"><span data-stu-id="d62b2-141">To specify multiple names, use commas to separate the names.</span></span>
<span data-ttu-id="d62b2-142">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d62b2-142">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d62b2-143">-Timeout</span><span class="sxs-lookup"><span data-stu-id="d62b2-143">-Timeout</span></span>

<span data-ttu-id="d62b2-144">指定此 Cmdlet 等候指定之處理程序停止的時間上限 (秒)。</span><span class="sxs-lookup"><span data-stu-id="d62b2-144">Specifies the maximum time, in seconds, that this cmdlet waits for the specified processes to stop.</span></span>
<span data-ttu-id="d62b2-145">當這個間隔時間過期時，此命令會顯示一個非終止錯誤，當中列出仍在執行的處理程序，然後結束等候。</span><span class="sxs-lookup"><span data-stu-id="d62b2-145">When this interval expires, the command displays a non-terminating error that lists the processes that are still running, and ends the wait.</span></span>
<span data-ttu-id="d62b2-146">預設是沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="d62b2-146">By default, there is no time-out.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d62b2-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d62b2-147">CommonParameters</span></span>

<span data-ttu-id="d62b2-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d62b2-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d62b2-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d62b2-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d62b2-150">輸入</span><span class="sxs-lookup"><span data-stu-id="d62b2-150">INPUTS</span></span>

### <span data-ttu-id="d62b2-151">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-151">System.Diagnostics.Process</span></span>

<span data-ttu-id="d62b2-152">您可以使用管線將處理程序物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d62b2-152">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="d62b2-153">輸出</span><span class="sxs-lookup"><span data-stu-id="d62b2-153">OUTPUTS</span></span>

### <span data-ttu-id="d62b2-154">無</span><span class="sxs-lookup"><span data-stu-id="d62b2-154">None</span></span>

<span data-ttu-id="d62b2-155">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d62b2-155">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d62b2-156">注意</span><span class="sxs-lookup"><span data-stu-id="d62b2-156">NOTES</span></span>

* <span data-ttu-id="d62b2-157">此 Cmdlet 會使用 System.Diagnostics.Process 類別的 **WaitForExit** 方法。</span><span class="sxs-lookup"><span data-stu-id="d62b2-157">This cmdlet uses the **WaitForExit** method of the System.Diagnostics.Process class.</span></span> <span data-ttu-id="d62b2-158">如需有關這個方法的詳細資訊，請參閱 Microsoft .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="d62b2-158">For more information about this method, see the Microsoft .NET Framework SDK.</span></span>

*

## <span data-ttu-id="d62b2-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="d62b2-159">RELATED LINKS</span></span>

[<span data-ttu-id="d62b2-160">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-160">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="d62b2-161">Get-Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-161">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="d62b2-162">Start-Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-162">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="d62b2-163">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-163">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="d62b2-164">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="d62b2-164">Wait-Process</span></span>](Wait-Process.md)
