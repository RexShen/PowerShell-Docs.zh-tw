---
title: Cmdlet 輸出的類型 |Microsoft Docs
ms.date: 01/18/2019
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.openlocfilehash: 8f761fdddd264b7c580c4a860081fdc5d2776ee7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786351"
---
# <a name="types-of-cmdlet-output"></a><span data-ttu-id="227d9-102">Cmdlet 輸出的類型</span><span class="sxs-lookup"><span data-stu-id="227d9-102">Types of cmdlet output</span></span>

<span data-ttu-id="227d9-103">PowerShell 提供數個方法，可由 Cmdlet 呼叫以產生輸出。</span><span class="sxs-lookup"><span data-stu-id="227d9-103">PowerShell provides several methods that can be called by cmdlets to generate output.</span></span> <span data-ttu-id="227d9-104">這些方法會使用特定的作業，將其輸出寫入特定的資料流程，例如成功的資料流程或錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="227d9-104">These methods use a specific operation to write their output to a specific data stream, such as the success data stream or the error data stream.</span></span> <span data-ttu-id="227d9-105">本文說明輸出的類型，以及用來產生它們的方法。</span><span class="sxs-lookup"><span data-stu-id="227d9-105">This article describes the types of output and the methods used to generate them.</span></span>

## <a name="types-of-output"></a><span data-ttu-id="227d9-106">輸出類型</span><span class="sxs-lookup"><span data-stu-id="227d9-106">Types of output</span></span>

### <a name="success-output"></a><span data-ttu-id="227d9-107">成功輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-107">Success output</span></span>

<span data-ttu-id="227d9-108">Cmdlet 可以藉由傳回管線中的下一個命令可以處理的物件，來報告成功。</span><span class="sxs-lookup"><span data-stu-id="227d9-108">Cmdlets can report success by returning an object that can be processed by the next command in the pipeline.</span></span> <span data-ttu-id="227d9-109">在 Cmdlet 成功執行其動作之後，此 Cmdlet 會呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="227d9-109">After the cmdlet has successfully performed its action, the cmdlet calls the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="227d9-110">我們建議您呼叫這個方法，而不是[PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) ，而不是您要的[. writeline 方法](/dotnet/api/System.Console.WriteLine)。</span><span class="sxs-lookup"><span data-stu-id="227d9-110">We recommend that you call this method instead of the [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) or [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methods.</span></span>

<span data-ttu-id="227d9-111">您可以針對通常不會傳回物件的 Cmdlet 提供**PassThru**切換參數。</span><span class="sxs-lookup"><span data-stu-id="227d9-111">You can provide a **PassThru** switch parameter for cmdlets that do not typically return objects.</span></span>
<span data-ttu-id="227d9-112">在命令列指定**PassThru**切換參數時，會要求 Cmdlet 傳回物件。</span><span class="sxs-lookup"><span data-stu-id="227d9-112">When the **PassThru** switch parameter is specified at the command line, the cmdlet is asked to return an object.</span></span> <span data-ttu-id="227d9-113">如需具有**PassThru**參數的 Cmdlet 範例，請參閱[新增-歷程記錄](/powershell/module/Microsoft.PowerShell.Core/Add-History)。</span><span class="sxs-lookup"><span data-stu-id="227d9-113">For an example of a cmdlet that has a **PassThru** parameter, see [Add-History](/powershell/module/Microsoft.PowerShell.Core/Add-History).</span></span>

### <a name="error-output"></a><span data-ttu-id="227d9-114">錯誤輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-114">Error output</span></span>

<span data-ttu-id="227d9-115">Cmdlet 可以報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="227d9-115">Cmdlets can report errors.</span></span> <span data-ttu-id="227d9-116">當發生終止錯誤時，此 Cmdlet 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="227d9-116">When a terminating error occurs, the cmdlet throws an exception.</span></span> <span data-ttu-id="227d9-117">當發生非終止錯誤時，指令程式會呼叫[CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，將錯誤記錄傳送至錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="227d9-117">When a non-terminating error occurs, the cmdlet calls the [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method to send an error record to the error data stream.</span></span> <span data-ttu-id="227d9-118">如需錯誤報表的詳細資訊，請參閱[錯誤報表概念](./error-reporting-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="227d9-118">For more information about error reporting, see [Error Reporting Concepts](./error-reporting-concepts.md).</span></span>

### <a name="verbose-output"></a><span data-ttu-id="227d9-119">詳細資訊輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-119">Verbose output</span></span>

<span data-ttu-id="227d9-120">Cmdlet 可以提供有用的資訊給您，而 Cmdlet 會藉由呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法來正確處理記錄。</span><span class="sxs-lookup"><span data-stu-id="227d9-120">Cmdlets can provide useful information to you while the cmdlet is correctly processing records by calling the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span> <span data-ttu-id="227d9-121">方法會產生詳細訊息，指出如何繼續執行動作。</span><span class="sxs-lookup"><span data-stu-id="227d9-121">The method generates verbose messages that indicate how the action is proceeding.</span></span>

<span data-ttu-id="227d9-122">根據預設，不會顯示詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-122">By default, verbose messages are not displayed.</span></span> <span data-ttu-id="227d9-123">執行 Cmdlet 時，您可以指定**Verbose**參數來顯示這些訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-123">You can specify the **Verbose** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="227d9-124">**Verbose**是適用于所有 Cmdlet 的通用參數。</span><span class="sxs-lookup"><span data-stu-id="227d9-124">**Verbose** is a common parameter that is available to all cmdlets.</span></span>

### <a name="progress-output"></a><span data-ttu-id="227d9-125">進度輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-125">Progress output</span></span>

<span data-ttu-id="227d9-126">當 Cmdlet 正在執行需要很長時間才能完成的工作（例如以遞迴方式複製目錄）時，Cmdlet 可以提供進度資訊給您。</span><span class="sxs-lookup"><span data-stu-id="227d9-126">Cmdlets can provide progress information to you when the cmdlet is performing tasks that take a long time to complete, such as copying a directory recursively.</span></span> <span data-ttu-id="227d9-127">若要顯示進度資訊，Cmdlet 會呼叫[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。</span><span class="sxs-lookup"><span data-stu-id="227d9-127">To display progress information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

### <a name="debug-output"></a><span data-ttu-id="227d9-128">Debug 輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-128">Debug output</span></span>

<span data-ttu-id="227d9-129">Cmdlet 可以提供在對 Cmdlet 程式碼進行疑難排解時很有説明的 debug 訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-129">Cmdlets can provide debug messages that are helpful when troubleshooting the cmdlet code.</span></span> <span data-ttu-id="227d9-130">若要顯示調試資訊，Cmdlet 會呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。</span><span class="sxs-lookup"><span data-stu-id="227d9-130">To display debug information the cmdlet calls the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span>

<span data-ttu-id="227d9-131">根據預設，不會顯示偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-131">By default, debug messages are not displayed.</span></span> <span data-ttu-id="227d9-132">執行 Cmdlet 時，您可以指定**Debug**參數來顯示這些訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-132">You can specify the **Debug** parameter when the cmdlet is run to display these messages.</span></span> <span data-ttu-id="227d9-133">**Debug**是可用於所有 Cmdlet 的通用參數。</span><span class="sxs-lookup"><span data-stu-id="227d9-133">**Debug** is a common parameter that is available to all cmdlets.</span></span>

### <a name="warning-output"></a><span data-ttu-id="227d9-134">警告輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-134">Warning output</span></span>

<span data-ttu-id="227d9-135">Cmdlet 可以藉由呼叫[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法來顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-135">Cmdlets can display warning messages by calling the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method.</span></span>

<span data-ttu-id="227d9-136">根據預設，會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-136">By default, warning messages are displayed.</span></span> <span data-ttu-id="227d9-137">不過，您可以使用 `$WarningPreference` 變數，或在呼叫 Cmdlet 時使用**Verbose**和**Debug**參數來設定警告訊息。</span><span class="sxs-lookup"><span data-stu-id="227d9-137">However, you can configure warning messages by using the `$WarningPreference` variable or by using the **Verbose** and **Debug** parameters when the cmdlet is called.</span></span>

## <a name="displaying-output"></a><span data-ttu-id="227d9-138">顯示輸出</span><span class="sxs-lookup"><span data-stu-id="227d9-138">Displaying output</span></span>

<span data-ttu-id="227d9-139">對於所有的寫入方法呼叫而言，內容顯示是由特定的執行時間變數所決定。</span><span class="sxs-lookup"><span data-stu-id="227d9-139">For all write-method calls, the content display is determined by specific runtime variables.</span></span> <span data-ttu-id="227d9-140">這個例外狀況是[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的。</span><span class="sxs-lookup"><span data-stu-id="227d9-140">The exception is the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span> <span data-ttu-id="227d9-141">藉由使用這些變數，您可以在程式碼中的正確位置進行適當的寫入呼叫，而不需要擔心輸出是否應該顯示。</span><span class="sxs-lookup"><span data-stu-id="227d9-141">By using these variables, you can make the appropriate write call at the correct place in your code and not worry about when or if the output should be displayed.</span></span>

## <a name="accessing-the-output-functionality-of-a-host-application"></a><span data-ttu-id="227d9-142">存取主應用程式的輸出功能</span><span class="sxs-lookup"><span data-stu-id="227d9-142">Accessing the output functionality of a host application</span></span>

<span data-ttu-id="227d9-143">您也可以設計 Cmdlet，透過 PowerShell 執行時間直接存取主應用程式的輸出功能。</span><span class="sxs-lookup"><span data-stu-id="227d9-143">You can also design a cmdlet to directly access the output functionality of a host application through the PowerShell runtime.</span></span> <span data-ttu-id="227d9-144">使用 PowerShell 所提供的主機 Api，而不是[system. 主控台](/dotnet/api/System.Console)或[system.web](/dotnet/api/System.Windows.Forms) ，可確保您的 Cmdlet 可與各種主機搭配使用。</span><span class="sxs-lookup"><span data-stu-id="227d9-144">Using the host APIs provided by PowerShell instead of [System.Console](/dotnet/api/System.Console) or [System.Windows.Forms](/dotnet/api/System.Windows.Forms) ensures that your cmdlet will work with a variety of hosts.</span></span> <span data-ttu-id="227d9-145">例如： **powershell.exe**主控台主機、 **powershell_ise.exe**圖形化主機、PowerShell 遠端主機和協力廠商主機。</span><span class="sxs-lookup"><span data-stu-id="227d9-145">For example: the **powershell.exe** console host, the **powershell_ise.exe** graphical host, the PowerShell remoting host, and third-party hosts.</span></span>

## <a name="see-also"></a><span data-ttu-id="227d9-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="227d9-146">See also</span></span>

[<span data-ttu-id="227d9-147">錯誤報告概念</span><span class="sxs-lookup"><span data-stu-id="227d9-147">Error Reporting Concepts</span></span>](./error-reporting-concepts.md)

[<span data-ttu-id="227d9-148">Cmdlet 概觀</span><span class="sxs-lookup"><span data-stu-id="227d9-148">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="227d9-149">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="227d9-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
