---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 參考-新功能
description: Windows PowerShell 參考-新功能
ms.openlocfilehash: b6fa97eacd476f055dd0c69eed2e547c450b85e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647121"
---
# <a name="whats-new"></a><span data-ttu-id="e9c31-103">新功能</span><span class="sxs-lookup"><span data-stu-id="e9c31-103">What's New</span></span>

<span data-ttu-id="e9c31-104">Windows PowerShell 2.0 提供下列新功能，可在撰寫 Cmdlet、提供者和主機應用程式時使用。</span><span class="sxs-lookup"><span data-stu-id="e9c31-104">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="e9c31-105">單元</span><span class="sxs-lookup"><span data-stu-id="e9c31-105">Modules</span></span>

<span data-ttu-id="e9c31-106">您現在可以使用模組封裝和散發 Windows PowerShell 的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e9c31-106">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="e9c31-107">模組可讓您分割、組織及抽象化 Windows PowerShell 程式碼，使其成為獨立、可重複使用的單位。</span><span class="sxs-lookup"><span data-stu-id="e9c31-107">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="e9c31-108">如需模組的詳細資訊，請參閱撰寫 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="e9c31-108">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="e9c31-109">PowerShell 類別</span><span class="sxs-lookup"><span data-stu-id="e9c31-109">The PowerShell class</span></span>

<span data-ttu-id="e9c31-110">PowerShell 類別提供更簡單的解決方案，可讓您以程式設計方式執行命令來建立應用程式，稱為主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9c31-110">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="e9c31-111">這個類別可讓您建立命令的管線、指定用來執行命令的運行時，以及指定以同步或非同步方式叫用命令。</span><span class="sxs-lookup"><span data-stu-id="e9c31-111">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="e9c31-112">RunspacePool 類別</span><span class="sxs-lookup"><span data-stu-id="e9c31-112">The RunspacePool class</span></span>

<span data-ttu-id="e9c31-113">運行空間集區可讓您使用單一呼叫來建立多個運行空間。</span><span class="sxs-lookup"><span data-stu-id="e9c31-113">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="e9c31-114">CreateRunspacePool 方法提供數個多載，可用來建立具有相同功能的多載，例如相同的主機、初始會話狀態和連接資訊。</span><span class="sxs-lookup"><span data-stu-id="e9c31-114">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="e9c31-115">>initialsessionstate 類別</span><span class="sxs-lookup"><span data-stu-id="e9c31-115">The InitialSessionState class</span></span>

<span data-ttu-id="e9c31-116">>initialsessionstate 類別可讓您建立在開啟配置空間時使用的會話狀態設定。</span><span class="sxs-lookup"><span data-stu-id="e9c31-116">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="e9c31-117">您可以建立自訂設定，這是預設設定，其中包含 mshshort 所提供的命令，以及根據會話的功能限制其命令的設定。</span><span class="sxs-lookup"><span data-stu-id="e9c31-117">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="e9c31-118">遠端空間</span><span class="sxs-lookup"><span data-stu-id="e9c31-118">Remote runspaces</span></span>

<span data-ttu-id="e9c31-119">您現在可以建立可在遠端電腦上開啟的執行程式，可讓您在遠端電腦上執行命令，並在本機收集結果。</span><span class="sxs-lookup"><span data-stu-id="e9c31-119">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="e9c31-120">若要建立遠端執行時間，您必須在建立執行時間時指定遠端連線的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e9c31-120">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="e9c31-121">如需範例，請參閱 CreateRunspace 和 CreateRunspacePool 方法。</span><span class="sxs-lookup"><span data-stu-id="e9c31-121">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="e9c31-122">連接資訊是由 RunspaceConnectionInfo 類別定義。</span><span class="sxs-lookup"><span data-stu-id="e9c31-122">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="e9c31-123">私用空間元素</span><span class="sxs-lookup"><span data-stu-id="e9c31-123">Private runspace elements</span></span>

<span data-ttu-id="e9c31-124">您現在可以建立其元素為公用或私用的空間。</span><span class="sxs-lookup"><span data-stu-id="e9c31-124">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="e9c31-125">這可讓您建立可供運行空間使用但無法供使用者使用的工作空間。</span><span class="sxs-lookup"><span data-stu-id="e9c31-125">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="e9c31-126">請參閱 ConstrainedSessionStateEntry 類別，找出可讓運行時的哪些元素成為私用。</span><span class="sxs-lookup"><span data-stu-id="e9c31-126">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="e9c31-127">運行時執行緒模式和單元狀態</span><span class="sxs-lookup"><span data-stu-id="e9c31-127">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="e9c31-128">您現在可以指定在執行時間中執行命令時，如何建立及使用執行緒。</span><span class="sxs-lookup"><span data-stu-id="e9c31-128">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="e9c31-129">請參閱 ThreadOptions 和 RunspacePool. ThreadOptions 屬性（此為內容）的內容（）。</span><span class="sxs-lookup"><span data-stu-id="e9c31-129">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="e9c31-130">您現在可以取得在執行空間中用來執行命令之執行緒的單元狀態。</span><span class="sxs-lookup"><span data-stu-id="e9c31-130">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="e9c31-131">請參閱 System.threading.thread.apartmentstate 和 RunspacePool. System.threading.thread.apartmentstate 屬性（此為內容）的內容（）。</span><span class="sxs-lookup"><span data-stu-id="e9c31-131">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="e9c31-132">Transaction Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e9c31-132">Transaction cmdlets</span></span>

<span data-ttu-id="e9c31-133">您現在可以建立可在交易內使用的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9c31-133">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="e9c31-134">在交易中使用 Cmdlet 時，其動作是暫時性的，而且 Windows PowerShell 所提供的交易 Cmdlet 可以接受或拒絕。</span><span class="sxs-lookup"><span data-stu-id="e9c31-134">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="e9c31-135">如需交易的詳細資訊，請參閱如何支援交易。</span><span class="sxs-lookup"><span data-stu-id="e9c31-135">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="e9c31-136">交易提供者</span><span class="sxs-lookup"><span data-stu-id="e9c31-136">Transaction provider</span></span>

<span data-ttu-id="e9c31-137">您現在可以建立可在交易內使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="e9c31-137">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="e9c31-138">類似于 Cmdlet，在交易中使用提供者時，它的動作是暫時性的，而且 Windows PowerShell 提供的交易 Cmdlet 可以接受或拒絕。</span><span class="sxs-lookup"><span data-stu-id="e9c31-138">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="e9c31-139">如需有關在提供者類別內指定交易支援的詳細資訊，請參閱 CmdletProviderAttribute ProviderCapabilities 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9c31-139">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="e9c31-140">作業 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e9c31-140">Job cmdlets</span></span>

<span data-ttu-id="e9c31-141">您現在可以撰寫可執行其動作做為作業的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9c31-141">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="e9c31-142">這些作業會在背景中執行，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="e9c31-142">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="e9c31-143">如需 Windows PowerShell 如何支援工作的詳細資訊，請參閱背景工作。</span><span class="sxs-lookup"><span data-stu-id="e9c31-143">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="e9c31-144">Cmdlet 輸出類型</span><span class="sxs-lookup"><span data-stu-id="e9c31-144">Cmdlet output types</span></span>

<span data-ttu-id="e9c31-145">您現在可以在撰寫 Cmdlet 時宣告 OutputType 屬性，藉以指定 Cmdlet 所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="e9c31-145">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="e9c31-146">這可讓其他人藉由查看 Cmdlet 的 OutputType 屬性來判斷 Cmdlet 所傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="e9c31-146">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="e9c31-147">事件支援</span><span class="sxs-lookup"><span data-stu-id="e9c31-147">Event support</span></span>

<span data-ttu-id="e9c31-148">您現在可以撰寫新增和取用事件的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9c31-148">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="e9c31-149">請參閱 PSEvent 類別。</span><span class="sxs-lookup"><span data-stu-id="e9c31-149">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="e9c31-150">Proxy 命令</span><span class="sxs-lookup"><span data-stu-id="e9c31-150">Proxy commands</span></span>

<span data-ttu-id="e9c31-151">您現在可以撰寫可用於執行另一個命令的 proxy 命令。</span><span class="sxs-lookup"><span data-stu-id="e9c31-151">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="e9c31-152">Proxy 命令可讓您控制使用者可以使用的來源 Cmdlet 功能。</span><span class="sxs-lookup"><span data-stu-id="e9c31-152">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="e9c31-153">例如，您可以建立 proxy 命令來移除 source 命令所提供的參數。</span><span class="sxs-lookup"><span data-stu-id="e9c31-153">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="e9c31-154">請參閱 ProxyCommand 類別。</span><span class="sxs-lookup"><span data-stu-id="e9c31-154">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="e9c31-155">多個選擇提示</span><span class="sxs-lookup"><span data-stu-id="e9c31-155">Multiple choice prompts</span></span>

<span data-ttu-id="e9c31-156">您現在可以撰寫可提供提示的應用程式，讓使用者選取多個選項。</span><span class="sxs-lookup"><span data-stu-id="e9c31-156">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="e9c31-157">查看 IHostUISupportsMultipleChoiceSelection 介面</span><span class="sxs-lookup"><span data-stu-id="e9c31-157">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="e9c31-158">互動式會話</span><span class="sxs-lookup"><span data-stu-id="e9c31-158">Interactive sessions</span></span>

<span data-ttu-id="e9c31-159">您現在可以撰寫應用程式，在遠端電腦上啟動及停止互動式會話。</span><span class="sxs-lookup"><span data-stu-id="e9c31-159">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="e9c31-160">請參閱 IHostSupportsInteractiveSession 介面。</span><span class="sxs-lookup"><span data-stu-id="e9c31-160">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="e9c31-161">提供者的自訂 Cmdlet 說明</span><span class="sxs-lookup"><span data-stu-id="e9c31-161">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="e9c31-162">您現在可以建立提供者 Cmdlet 的自訂說明主題。</span><span class="sxs-lookup"><span data-stu-id="e9c31-162">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="e9c31-163">自訂的 Cmdlet 說明主題可解釋 Cmdlet 在提供者路徑中的運作方式，以及檔特殊功能，包括提供者新增至 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="e9c31-163">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>
