---
title: Windows PowerShell 參考-新功能
ms.date: 09/13/2016
ms.openlocfilehash: 4e87fce34f74e0fcbfe25939e1555df308a7f7d0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786691"
---
# <a name="whats-new"></a><span data-ttu-id="8fefa-102">新功能</span><span class="sxs-lookup"><span data-stu-id="8fefa-102">What's New</span></span>

<span data-ttu-id="8fefa-103">Windows PowerShell 2.0 提供下列新功能，以便在撰寫 Cmdlet、提供者和主機應用程式時使用。</span><span class="sxs-lookup"><span data-stu-id="8fefa-103">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="8fefa-104">模組</span><span class="sxs-lookup"><span data-stu-id="8fefa-104">Modules</span></span>

<span data-ttu-id="8fefa-105">您現在可以使用模組來封裝和散發 Windows PowerShell 解決方案。</span><span class="sxs-lookup"><span data-stu-id="8fefa-105">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="8fefa-106">模組可讓您將 Windows PowerShell 程式碼分割、組織及抽象化成獨立、可重複使用的單位。</span><span class="sxs-lookup"><span data-stu-id="8fefa-106">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="8fefa-107">如需模組的詳細資訊，請參閱撰寫 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="8fefa-107">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="8fefa-108">PowerShell 類別</span><span class="sxs-lookup"><span data-stu-id="8fefa-108">The PowerShell class</span></span>

<span data-ttu-id="8fefa-109">PowerShell 類別提供更簡單的解決方案，讓您建立以程式設計方式執行命令的應用程式（稱為「主機應用程式」）。</span><span class="sxs-lookup"><span data-stu-id="8fefa-109">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="8fefa-110">這個類別可讓您建立命令的管線、指定用來執行命令的運行時，以及指定以同步或非同步方式叫用命令。</span><span class="sxs-lookup"><span data-stu-id="8fefa-110">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="8fefa-111">RunspacePool 類別</span><span class="sxs-lookup"><span data-stu-id="8fefa-111">The RunspacePool class</span></span>

<span data-ttu-id="8fefa-112">「運行空間集區」可讓您使用單一呼叫來建立多個運行空間。</span><span class="sxs-lookup"><span data-stu-id="8fefa-112">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="8fefa-113">CreateRunspacePool 方法提供數個多載，可用來建立具有相同功能（例如，相同的主機、初始會話狀態和連接資訊）的工作空間。</span><span class="sxs-lookup"><span data-stu-id="8fefa-113">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="8fefa-114">InitialSessionState 類別</span><span class="sxs-lookup"><span data-stu-id="8fefa-114">The InitialSessionState class</span></span>

<span data-ttu-id="8fefa-115">InitialSessionState 類別可讓您建立在開啟執行時間時使用的會話狀態設定。</span><span class="sxs-lookup"><span data-stu-id="8fefa-115">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="8fefa-116">您可以建立自訂設定、包含 mshshort 所提供命令的預設設定，以及根據會話功能限制其命令的設定。</span><span class="sxs-lookup"><span data-stu-id="8fefa-116">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="8fefa-117">遠端空間</span><span class="sxs-lookup"><span data-stu-id="8fefa-117">Remote runspaces</span></span>

<span data-ttu-id="8fefa-118">您現在可以建立可在遠端電腦上開啟的執行空間，讓您在遠端電腦上執行命令，並在本機收集結果。</span><span class="sxs-lookup"><span data-stu-id="8fefa-118">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="8fefa-119">若要建立遠端執行時間，您必須在建立執行時間時指定遠端連線的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8fefa-119">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="8fefa-120">如需範例，請參閱 CreateRunspace 和 CreateRunspacePool 方法。</span><span class="sxs-lookup"><span data-stu-id="8fefa-120">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="8fefa-121">連接資訊是由 RunspaceConnectionInfo 類別所定義。</span><span class="sxs-lookup"><span data-stu-id="8fefa-121">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="8fefa-122">私用的運行空間元素</span><span class="sxs-lookup"><span data-stu-id="8fefa-122">Private runspace elements</span></span>

<span data-ttu-id="8fefa-123">您現在可以建立其元素為公用或私用的使用者空間。</span><span class="sxs-lookup"><span data-stu-id="8fefa-123">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="8fefa-124">這可讓您建立其元素可供運行空間使用，但無法供使用者使用的工作空間。</span><span class="sxs-lookup"><span data-stu-id="8fefa-124">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="8fefa-125">請參閱 ConstrainedSessionStateEntry 類別，找出可將運行空間的哪些元素設為私用。</span><span class="sxs-lookup"><span data-stu-id="8fefa-125">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="8fefa-126">運行空間執行緒模式和單元狀態</span><span class="sxs-lookup"><span data-stu-id="8fefa-126">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="8fefa-127">您現在可以指定在執行時間中執行命令時，如何建立及使用執行緒。</span><span class="sxs-lookup"><span data-stu-id="8fefa-127">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="8fefa-128">請參閱 ThreadOptions 和 RunspacePool. ThreadOptions 屬性（此為系統管理的內容。）。</span><span class="sxs-lookup"><span data-stu-id="8fefa-128">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="8fefa-129">您現在可以取得在運行空間中用來執行命令之執行緒的單元狀態。</span><span class="sxs-lookup"><span data-stu-id="8fefa-129">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="8fefa-130">請參閱 System.threading.thread.apartmentstate 和 RunspacePool. System.threading.thread.apartmentstate 屬性（此為系統管理的內容。）。</span><span class="sxs-lookup"><span data-stu-id="8fefa-130">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="8fefa-131">交易 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8fefa-131">Transaction cmdlets</span></span>

<span data-ttu-id="8fefa-132">您現在可以建立可在交易內使用的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fefa-132">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="8fefa-133">在交易中使用 Cmdlet 時，其動作是暫時性的，而且可以由 Windows PowerShell 所提供的交易 Cmdlet 接受或拒絕。</span><span class="sxs-lookup"><span data-stu-id="8fefa-133">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="8fefa-134">如需交易的詳細資訊，請參閱如何支援交易。</span><span class="sxs-lookup"><span data-stu-id="8fefa-134">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="8fefa-135">交易提供者</span><span class="sxs-lookup"><span data-stu-id="8fefa-135">Transaction provider</span></span>

<span data-ttu-id="8fefa-136">您現在可以建立可在交易中使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="8fefa-136">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="8fefa-137">類似于 Cmdlet，在交易中使用提供者時，其動作是暫時性的，而且可以由 Windows PowerShell 所提供的交易 Cmdlet 接受或拒絕。</span><span class="sxs-lookup"><span data-stu-id="8fefa-137">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="8fefa-138">如需在提供者類別中指定交易支援的詳細資訊，請參閱 CmdletProviderAttribute. ProviderCapabilities 屬性。</span><span class="sxs-lookup"><span data-stu-id="8fefa-138">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="8fefa-139">作業 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8fefa-139">Job cmdlets</span></span>

<span data-ttu-id="8fefa-140">您現在可以撰寫可將其動作當做作業執行的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fefa-140">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="8fefa-141">這些作業會在背景執行，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="8fefa-141">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="8fefa-142">如需 Windows PowerShell 如何支援作業的詳細資訊，請參閱背景工作。</span><span class="sxs-lookup"><span data-stu-id="8fefa-142">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="8fefa-143">Cmdlet 輸出類型</span><span class="sxs-lookup"><span data-stu-id="8fefa-143">Cmdlet output types</span></span>

<span data-ttu-id="8fefa-144">您現在可以在撰寫 Cmdlet 時宣告 OutputType 屬性，藉以指定 Cmdlet 所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="8fefa-144">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="8fefa-145">這可讓其他人藉由查看 Cmdlet 的 OutputType 屬性，來判斷 Cmdlet 所傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="8fefa-145">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="8fefa-146">事件支援</span><span class="sxs-lookup"><span data-stu-id="8fefa-146">Event support</span></span>

<span data-ttu-id="8fefa-147">您現在可以撰寫可新增和使用事件的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fefa-147">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="8fefa-148">請參閱 PSEvent 類別。</span><span class="sxs-lookup"><span data-stu-id="8fefa-148">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="8fefa-149">Proxy 命令</span><span class="sxs-lookup"><span data-stu-id="8fefa-149">Proxy commands</span></span>

<span data-ttu-id="8fefa-150">您現在可以撰寫可用於執行另一個命令的 proxy 命令。</span><span class="sxs-lookup"><span data-stu-id="8fefa-150">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="8fefa-151">Proxy 命令可讓您控制哪些來源 Cmdlet 的功能可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="8fefa-151">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="8fefa-152">例如，您可以建立 proxy 命令來移除 source 命令所提供的參數。</span><span class="sxs-lookup"><span data-stu-id="8fefa-152">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="8fefa-153">請參閱 ProxyCommand 類別。</span><span class="sxs-lookup"><span data-stu-id="8fefa-153">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="8fefa-154">多重選取提示</span><span class="sxs-lookup"><span data-stu-id="8fefa-154">Multiple choice prompts</span></span>

<span data-ttu-id="8fefa-155">您現在可以撰寫可提供提示的應用程式，讓使用者選取多個選項。</span><span class="sxs-lookup"><span data-stu-id="8fefa-155">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="8fefa-156">請參閱 IHostUISupportsMultipleChoiceSelection 介面</span><span class="sxs-lookup"><span data-stu-id="8fefa-156">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="8fefa-157">互動式會話</span><span class="sxs-lookup"><span data-stu-id="8fefa-157">Interactive sessions</span></span>

<span data-ttu-id="8fefa-158">您現在可以撰寫可在遠端電腦上啟動和停止互動式會話的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8fefa-158">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="8fefa-159">請參閱 IHostSupportsInteractiveSession 介面。</span><span class="sxs-lookup"><span data-stu-id="8fefa-159">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="8fefa-160">提供者的自訂 Cmdlet 說明</span><span class="sxs-lookup"><span data-stu-id="8fefa-160">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="8fefa-161">您現在可以建立提供者 Cmdlet 的自訂說明主題。</span><span class="sxs-lookup"><span data-stu-id="8fefa-161">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="8fefa-162">自訂 Cmdlet 說明主題可以說明此 Cmdlet 在提供者路徑中的運作方式，以及檔特殊功能，包括提供者新增至 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="8fefa-162">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>
