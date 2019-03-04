---
title: 類型的 Cmdlet 輸出 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853924"
---
# <a name="types-of-cmdlet-output"></a><span data-ttu-id="bf547-102">類型的 cmdlet 輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-102">Types of cmdlet output</span></span>

<span data-ttu-id="bf547-103">PowerShell 提供數種方法，可呼叫指令程式來產生輸出。</span><span class="sxs-lookup"><span data-stu-id="bf547-103">PowerShell provides several methods that can be called by cmdlets to generate output.</span></span> <span data-ttu-id="bf547-104">這些方法會使用特定的作業，將其輸出寫入至特定的資料流，例如成功的資料流或錯誤資料流。</span><span class="sxs-lookup"><span data-stu-id="bf547-104">These methods use a specific operation to write their output to a specific data stream, such as the success data stream or the error data stream.</span></span> <span data-ttu-id="bf547-105">本文說明輸出和用來產生這些方法的類型。</span><span class="sxs-lookup"><span data-stu-id="bf547-105">This article describes the types of output and the methods used to generate them.</span></span>

## <a name="types-of-output"></a><span data-ttu-id="bf547-106">類型的輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-106">Types of output</span></span>

### <a name="success-output"></a><span data-ttu-id="bf547-107">成功輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-107">Success output</span></span>

<span data-ttu-id="bf547-108">Cmdlet 可以藉由傳回的物件，可處理的管線中下一個命令會報告成功。</span><span class="sxs-lookup"><span data-stu-id="bf547-108">Cmdlets can report success by returning an object that can be processed by the next command in the pipeline.</span></span> <span data-ttu-id="bf547-109">此指令程式已成功執行其動作之後，cmdlet 就會呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-109">After the cmdlet has successfully performed its action, the cmdlet calls the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="bf547-110">我們建議您呼叫此方法，而非[System.Console.WriteLine](/dotnet/api/System.Console.WriteLine)或是[System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-110">We recommend that you call this method instead of the [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) or [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methods.</span></span>

<span data-ttu-id="bf547-111">您可以提供**PassThru**切換通常不會傳回物件的 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="bf547-111">You can provide a **PassThru** switch parameter for cmdlets that do not typically return objects.</span></span>
<span data-ttu-id="bf547-112">當**PassThru**在命令列指定切換參數，cmdlet 會要求傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="bf547-112">When the **PassThru** switch parameter is specified at the command line, the cmdlet is asked to return an object.</span></span> <span data-ttu-id="bf547-113">如需範例指令程式可**PassThru**參數，請參閱[Add-history](/powershell/module/Microsoft.PowerShell.Core/Add-History)。</span><span class="sxs-lookup"><span data-stu-id="bf547-113">For an example of a cmdlet that has a **PassThru** parameter, see [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).</span></span>

### <a name="error-output"></a><span data-ttu-id="bf547-114">錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-114">Error output</span></span>

<span data-ttu-id="bf547-115">Cmdlet 可以報告的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf547-115">Cmdlets can report errors.</span></span> <span data-ttu-id="bf547-116">終止錯誤發生時，此指令程式會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf547-116">When a terminating error occurs, the cmdlet throws an exception.</span></span> <span data-ttu-id="bf547-117">發生非終止錯誤時，cmdlet 就會呼叫[System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，將錯誤記錄傳送至錯誤資料流。</span><span class="sxs-lookup"><span data-stu-id="bf547-117">When a non-terminating error occurs, the cmdlet calls the [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method to send an error record to the error data stream.</span></span> <span data-ttu-id="bf547-118">如需有關錯誤報告的詳細資訊，請參閱 <<c0> [ 錯誤報告概念](./error-reporting-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="bf547-118">For more information about error reporting, see [Error Reporting Concepts](./error-reporting-concepts.md).</span></span>

### <a name="verbose-output"></a><span data-ttu-id="bf547-119">詳細資訊輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-119">Verbose output</span></span>

<span data-ttu-id="bf547-120">Cmdlet 可以提供有用的資訊給您時 cmdlet 呼叫中正確處理資料錄[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-120">Cmdlets can provide useful information to you while the cmdlet is correctly processing records by calling the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span> <span data-ttu-id="bf547-121">此方法會產生詳細的訊息，指出動作正在進行的方式。</span><span class="sxs-lookup"><span data-stu-id="bf547-121">The method generates verbose messages that indicate how the action is proceeding.</span></span>

<span data-ttu-id="bf547-122">根據預設，將不會顯示詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="bf547-122">By default, verbose messages are not displayed.</span></span> <span data-ttu-id="bf547-123">您可以指定**Verbose**時，此 cmdlet 會執行，以顯示這些訊息。</span><span class="sxs-lookup"><span data-stu-id="bf547-123">You can specify the **Verbose** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="bf547-124">**Verbose**是常見的參數所使用的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf547-124">**Verbose** is a common parameter that is available to all cmdlets.</span></span>

### <a name="progress-output"></a><span data-ttu-id="bf547-125">進度輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-125">Progress output</span></span>

<span data-ttu-id="bf547-126">Cmdlet 可以將進度資訊提供給您，當 cmdlet 執行工作都要花很長的時間才能完成，例如目錄遞迴複製。</span><span class="sxs-lookup"><span data-stu-id="bf547-126">Cmdlets can provide progress information to you when the cmdlet is performing tasks that take a long time to complete, such as copying a directory recursively.</span></span> <span data-ttu-id="bf547-127">若要顯示進度資訊指令程式會呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-127">To display progress information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

### <a name="debug-output"></a><span data-ttu-id="bf547-128">偵錯輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-128">Debug output</span></span>

<span data-ttu-id="bf547-129">Cmdlet 可以提供疑難排解 cmdlet 程式碼時很有幫助的偵錯訊息。</span><span class="sxs-lookup"><span data-stu-id="bf547-129">Cmdlets can provide debug messages that are helpful when troubleshooting the cmdlet code.</span></span> <span data-ttu-id="bf547-130">若要顯示偵錯資訊的指令程式會呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-130">To display debug information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span>

<span data-ttu-id="bf547-131">根據預設，不會顯示偵錯訊息。</span><span class="sxs-lookup"><span data-stu-id="bf547-131">By default, debug messages are not displayed.</span></span> <span data-ttu-id="bf547-132">您可以指定**偵錯**時，此 cmdlet 會執行，以顯示這些訊息。</span><span class="sxs-lookup"><span data-stu-id="bf547-132">You can specify the **Debug** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="bf547-133">**偵錯**是常見的參數所使用的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf547-133">**Debug** is a common parameter that is available to all cmdlets.</span></span>

### <a name="warning-output"></a><span data-ttu-id="bf547-134">警告輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-134">Warning output</span></span>

<span data-ttu-id="bf547-135">Cmdlet 可以顯示警告訊息，藉由呼叫[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-135">Cmdlets can display warning messages by calling the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

<span data-ttu-id="bf547-136">根據預設，會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="bf547-136">By default, warning messages are displayed.</span></span> <span data-ttu-id="bf547-137">不過，您可以設定警告訊息，利用`$WarningPreference`變數，或使用**Verbose**並**偵錯**參數呼叫 cmdlet 時。</span><span class="sxs-lookup"><span data-stu-id="bf547-137">However, you can configure warning messages by using the `$WarningPreference` variable or by using the **Verbose** and **Debug** parameters when the cmdlet is called.</span></span>

## <a name="displaying-output"></a><span data-ttu-id="bf547-138">顯示輸出</span><span class="sxs-lookup"><span data-stu-id="bf547-138">Displaying output</span></span>

<span data-ttu-id="bf547-139">針對所有寫入方法呼叫，內容顯示由特定執行階段變數決定。</span><span class="sxs-lookup"><span data-stu-id="bf547-139">For all write-method calls, the content display is determined by specific runtime variables.</span></span> <span data-ttu-id="bf547-140">例外狀況[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="bf547-140">The exception is the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="bf547-141">藉由使用這些變數，您可以進行適當的程式碼中寫入的正確位置的呼叫，而不必擔心時，或應該會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="bf547-141">By using these variables, you can make the appropriate write call at the correct place in your code and not worry about when or if the output should be displayed.</span></span>

## <a name="accessing-the-output-functionality-of-a-host-application"></a><span data-ttu-id="bf547-142">存取主應用程式的輸出功能</span><span class="sxs-lookup"><span data-stu-id="bf547-142">Accessing the output functionality of a host application</span></span>

<span data-ttu-id="bf547-143">您也可以設計可直接透過 PowerShell 執行階段存取主應用程式的輸出功能的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf547-143">You can also design a cmdlet to directly access the output functionality of a host application through the PowerShell runtime.</span></span> <span data-ttu-id="bf547-144">使用主應用程式而不是 PowerShell 所提供的 Api [System.Console](/dotnet/api/System.Console)或是[System.Windows.Forms](/dotnet/api/System.Windows.Forms)可確保您的 cmdlet 會使用各種不同的主機。</span><span class="sxs-lookup"><span data-stu-id="bf547-144">Using the host APIs provided by PowerShell instead of [System.Console](/dotnet/api/System.Console) or [System.Windows.Forms](/dotnet/api/System.Windows.Forms) ensures that your cmdlet will work with a variety of hosts.</span></span> <span data-ttu-id="bf547-145">例如： **powershell.exe**主控台主機**powershell_ise.exe**圖形化的主機、 PowerShell 遠端處理主應用程式和協力廠商主機。</span><span class="sxs-lookup"><span data-stu-id="bf547-145">For example: the **powershell.exe** console host, the **powershell_ise.exe** graphical host, the PowerShell remoting host, and third-party hosts.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf547-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf547-146">See also</span></span>

[<span data-ttu-id="bf547-147">錯誤報告的概念</span><span class="sxs-lookup"><span data-stu-id="bf547-147">Error Reporting Concepts</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="bf547-148">指令程式概觀</span><span class="sxs-lookup"><span data-stu-id="bf547-148">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="bf547-149">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bf547-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)