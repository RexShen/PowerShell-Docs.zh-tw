---
ms.date: 01/18/2019
ms.topic: reference
title: Cmdlet 輸出類型
description: Cmdlet 輸出類型
ms.openlocfilehash: 591b7699e951db9016e48d5ef623265e23791e11
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660495"
---
# <a name="types-of-cmdlet-output"></a><span data-ttu-id="933a1-103">Cmdlet 輸出的類型</span><span class="sxs-lookup"><span data-stu-id="933a1-103">Types of cmdlet output</span></span>

<span data-ttu-id="933a1-104">PowerShell 提供數個方法，可由 Cmdlet 呼叫以產生輸出。</span><span class="sxs-lookup"><span data-stu-id="933a1-104">PowerShell provides several methods that can be called by cmdlets to generate output.</span></span> <span data-ttu-id="933a1-105">這些方法會使用特定的作業，將其輸出寫入至特定資料流程，例如成功資料流程或錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="933a1-105">These methods use a specific operation to write their output to a specific data stream, such as the success data stream or the error data stream.</span></span> <span data-ttu-id="933a1-106">本文說明輸出的類型以及用來產生它們的方法。</span><span class="sxs-lookup"><span data-stu-id="933a1-106">This article describes the types of output and the methods used to generate them.</span></span>

## <a name="types-of-output"></a><span data-ttu-id="933a1-107">輸出類型</span><span class="sxs-lookup"><span data-stu-id="933a1-107">Types of output</span></span>

### <a name="success-output"></a><span data-ttu-id="933a1-108">成功輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-108">Success output</span></span>

<span data-ttu-id="933a1-109">Cmdlet 可以藉由傳回管線中的下一個命令可處理的物件，來報告成功。</span><span class="sxs-lookup"><span data-stu-id="933a1-109">Cmdlets can report success by returning an object that can be processed by the next command in the pipeline.</span></span> <span data-ttu-id="933a1-110">指令程式成功執行其動作之後，指令程式會呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法。</span><span class="sxs-lookup"><span data-stu-id="933a1-110">After the cmdlet has successfully performed its action, the cmdlet calls the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="933a1-111">我們建議您呼叫這個方法，而不是[PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) ，而不是呼叫[ writeline 方法](/dotnet/api/System.Console.WriteLine)。</span><span class="sxs-lookup"><span data-stu-id="933a1-111">We recommend that you call this method instead of the [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) or [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methods.</span></span>

<span data-ttu-id="933a1-112">您可以針對通常不會傳回物件的 Cmdlet 提供 **PassThru** 切換參數。</span><span class="sxs-lookup"><span data-stu-id="933a1-112">You can provide a **PassThru** switch parameter for cmdlets that do not typically return objects.</span></span>
<span data-ttu-id="933a1-113">當您在命令列指定 **PassThru** 切換參數時，系統會要求 Cmdlet 傳回物件。</span><span class="sxs-lookup"><span data-stu-id="933a1-113">When the **PassThru** switch parameter is specified at the command line, the cmdlet is asked to return an object.</span></span> <span data-ttu-id="933a1-114">如需具有 **PassThru** 參數的 Cmdlet 範例，請參閱新增歷程 [記錄](/powershell/module/Microsoft.PowerShell.Core/Add-History)。</span><span class="sxs-lookup"><span data-stu-id="933a1-114">For an example of a cmdlet that has a **PassThru** parameter, see [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).</span></span>

### <a name="error-output"></a><span data-ttu-id="933a1-115">錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-115">Error output</span></span>

<span data-ttu-id="933a1-116">Cmdlet 可以報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="933a1-116">Cmdlets can report errors.</span></span> <span data-ttu-id="933a1-117">當終止錯誤發生時，此 Cmdlet 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="933a1-117">When a terminating error occurs, the cmdlet throws an exception.</span></span> <span data-ttu-id="933a1-118">當非終止錯誤發生時，此 Cmdlet 會呼叫 [CmdletProvider WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 方法，以將錯誤記錄傳送至錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="933a1-118">When a non-terminating error occurs, the cmdlet calls the [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method to send an error record to the error data stream.</span></span> <span data-ttu-id="933a1-119">如需有關錯誤報表的詳細資訊，請參閱 [錯誤報表概念](./error-reporting-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="933a1-119">For more information about error reporting, see [Error Reporting Concepts](./error-reporting-concepts.md).</span></span>

### <a name="verbose-output"></a><span data-ttu-id="933a1-120">詳細資訊輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-120">Verbose output</span></span>

<span data-ttu-id="933a1-121">Cmdlet 可以藉由呼叫 [WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 方法來正確處理記錄，以提供實用的資訊給您。</span><span class="sxs-lookup"><span data-stu-id="933a1-121">Cmdlets can provide useful information to you while the cmdlet is correctly processing records by calling the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span> <span data-ttu-id="933a1-122">方法會產生詳細訊息，指出動作如何進行。</span><span class="sxs-lookup"><span data-stu-id="933a1-122">The method generates verbose messages that indicate how the action is proceeding.</span></span>

<span data-ttu-id="933a1-123">依預設，不會顯示詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="933a1-123">By default, verbose messages are not displayed.</span></span> <span data-ttu-id="933a1-124">您可以在執行 Cmdlet 來顯示這些訊息時，指定 **Verbose** 參數。</span><span class="sxs-lookup"><span data-stu-id="933a1-124">You can specify the **Verbose** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="933a1-125">**Verbose** 是適用于所有 Cmdlet 的通用參數。</span><span class="sxs-lookup"><span data-stu-id="933a1-125">**Verbose** is a common parameter that is available to all cmdlets.</span></span>

### <a name="progress-output"></a><span data-ttu-id="933a1-126">進度輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-126">Progress output</span></span>

<span data-ttu-id="933a1-127">Cmdlet 可以在 Cmdlet 正在執行需要很長時間才能完成的工作（例如，以遞迴方式複製目錄）時，提供進度資訊給您。</span><span class="sxs-lookup"><span data-stu-id="933a1-127">Cmdlets can provide progress information to you when the cmdlet is performing tasks that take a long time to complete, such as copying a directory recursively.</span></span> <span data-ttu-id="933a1-128">若要顯示進度資訊，Cmdlet 會呼叫 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 方法。</span><span class="sxs-lookup"><span data-stu-id="933a1-128">To display progress information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

### <a name="debug-output"></a><span data-ttu-id="933a1-129">調試輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-129">Debug output</span></span>

<span data-ttu-id="933a1-130">Cmdlet 可以提供在疑難排解 Cmdlet 程式碼時很有説明的偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="933a1-130">Cmdlets can provide debug messages that are helpful when troubleshooting the cmdlet code.</span></span> <span data-ttu-id="933a1-131">為了顯示 debug 資訊，Cmdlet 會呼叫 [WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法。</span><span class="sxs-lookup"><span data-stu-id="933a1-131">To display debug information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span>

<span data-ttu-id="933a1-132">預設不會顯示 debug 訊息。</span><span class="sxs-lookup"><span data-stu-id="933a1-132">By default, debug messages are not displayed.</span></span> <span data-ttu-id="933a1-133">您可以在執行 Cmdlet 時指定 **Debug** 參數，以顯示這些訊息。</span><span class="sxs-lookup"><span data-stu-id="933a1-133">You can specify the **Debug** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="933a1-134">**Debug** 是可用於所有 Cmdlet 的通用參數。</span><span class="sxs-lookup"><span data-stu-id="933a1-134">**Debug** is a common parameter that is available to all cmdlets.</span></span>

### <a name="warning-output"></a><span data-ttu-id="933a1-135">警告輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-135">Warning output</span></span>

<span data-ttu-id="933a1-136">Cmdlet 可以藉由呼叫 [WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 方法來顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="933a1-136">Cmdlets can display warning messages by calling the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

<span data-ttu-id="933a1-137">根據預設，會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="933a1-137">By default, warning messages are displayed.</span></span> <span data-ttu-id="933a1-138">不過，您可以使用變數來設定警告訊息， `$WarningPreference` 或是在呼叫 Cmdlet 時使用 **Verbose** 和 **Debug** 參數。</span><span class="sxs-lookup"><span data-stu-id="933a1-138">However, you can configure warning messages by using the `$WarningPreference` variable or by using the **Verbose** and **Debug** parameters when the cmdlet is called.</span></span>

## <a name="displaying-output"></a><span data-ttu-id="933a1-139">顯示輸出</span><span class="sxs-lookup"><span data-stu-id="933a1-139">Displaying output</span></span>

<span data-ttu-id="933a1-140">針對所有的寫入方法呼叫，內容顯示是由特定的執行時間變數所決定。</span><span class="sxs-lookup"><span data-stu-id="933a1-140">For all write-method calls, the content display is determined by specific runtime variables.</span></span> <span data-ttu-id="933a1-141">[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的例外狀況為例外。</span><span class="sxs-lookup"><span data-stu-id="933a1-141">The exception is the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="933a1-142">藉由使用這些變數，您可以在程式碼中的正確位置進行適當的寫入呼叫，而不需要擔心何時或是否應顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="933a1-142">By using these variables, you can make the appropriate write call at the correct place in your code and not worry about when or if the output should be displayed.</span></span>

## <a name="accessing-the-output-functionality-of-a-host-application"></a><span data-ttu-id="933a1-143">存取主應用程式的輸出功能</span><span class="sxs-lookup"><span data-stu-id="933a1-143">Accessing the output functionality of a host application</span></span>

<span data-ttu-id="933a1-144">您也可以設計 Cmdlet，透過 PowerShell 執行時間直接存取主機應用程式的輸出功能。</span><span class="sxs-lookup"><span data-stu-id="933a1-144">You can also design a cmdlet to directly access the output functionality of a host application through the PowerShell runtime.</span></span> <span data-ttu-id="933a1-145">使用 PowerShell 提供的主機 Api （而不是 [系統主控台](/dotnet/api/System.Console) 或 system.string），可確保您的 Cmdlet [將可搭配](/dotnet/api/System.Windows.Forms) 各種主機使用。</span><span class="sxs-lookup"><span data-stu-id="933a1-145">Using the host APIs provided by PowerShell instead of [System.Console](/dotnet/api/System.Console) or [System.Windows.Forms](/dotnet/api/System.Windows.Forms) ensures that your cmdlet will work with a variety of hosts.</span></span> <span data-ttu-id="933a1-146">例如： **powershell.exe** 主控台主機、 **powershell_ise.exe** 圖形化主機、PowerShell 遠端主機和協力廠商主機。</span><span class="sxs-lookup"><span data-stu-id="933a1-146">For example: the **powershell.exe** console host, the **powershell_ise.exe** graphical host, the PowerShell remoting host, and third-party hosts.</span></span>

## <a name="see-also"></a><span data-ttu-id="933a1-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="933a1-147">See also</span></span>

[<span data-ttu-id="933a1-148">錯誤報告概念</span><span class="sxs-lookup"><span data-stu-id="933a1-148">Error Reporting Concepts</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="933a1-149">Cmdlet 概觀</span><span class="sxs-lookup"><span data-stu-id="933a1-149">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="933a1-150">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="933a1-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
