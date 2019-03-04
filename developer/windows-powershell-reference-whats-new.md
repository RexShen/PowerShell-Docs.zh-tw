---
title: Windows PowerShell 參考-最新消息
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858544"
---
# <a name="whats-new"></a><span data-ttu-id="46fc4-102">新功能</span><span class="sxs-lookup"><span data-stu-id="46fc4-102">What's New</span></span>

<span data-ttu-id="46fc4-103">Windows PowerShell 2.0 在撰寫 cmdlet、 提供者，以及裝載應用程式時，會提供使用的下列新功能。</span><span class="sxs-lookup"><span data-stu-id="46fc4-103">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="46fc4-104">模組</span><span class="sxs-lookup"><span data-stu-id="46fc4-104">Modules</span></span>

<span data-ttu-id="46fc4-105">您現在可以封裝，並使用模組來散發 Windows PowerShell 解決方案。</span><span class="sxs-lookup"><span data-stu-id="46fc4-105">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="46fc4-106">模組可讓您將資料分割、 組織和擷取成獨立、 可重複使用單位的 Windows PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="46fc4-106">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="46fc4-107">如需有關模組的詳細資訊，請參閱 < 撰寫 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="46fc4-107">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="46fc4-108">PowerShell 類別</span><span class="sxs-lookup"><span data-stu-id="46fc4-108">The PowerShell class</span></span>

<span data-ttu-id="46fc4-109">PowerShell 類別會提供較簡單的解決方案，來建立應用程式，稱為主機應用程式，以程式設計方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="46fc4-109">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="46fc4-110">這個類別可讓您建立的命令的管線，指定用來執行命令，runspace 並指定同步或非同步方式叫用命令。</span><span class="sxs-lookup"><span data-stu-id="46fc4-110">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="46fc4-111">RunspacePool 類別</span><span class="sxs-lookup"><span data-stu-id="46fc4-111">The RunspacePool class</span></span>

<span data-ttu-id="46fc4-112">Runspace 集區可讓您使用的單一呼叫中建立多個執行空間。</span><span class="sxs-lookup"><span data-stu-id="46fc4-112">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="46fc4-113">CreateRunspacePool 方法會提供可用來建立具有相同的功能，例如相同的主機、 初始工作階段狀態和連接資訊的 runspace 的數個多載。</span><span class="sxs-lookup"><span data-stu-id="46fc4-113">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="46fc4-114">InitialSessionState 類別</span><span class="sxs-lookup"><span data-stu-id="46fc4-114">The InitialSessionState class</span></span>

<span data-ttu-id="46fc4-115">InitialSessionState 類別可讓您建立 runspace 開啟時，會使用工作階段狀態設定。</span><span class="sxs-lookup"><span data-stu-id="46fc4-115">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="46fc4-116">您可以建立自訂的組態、 包含 mshshort，所提供的命令的預設組態和設定其命令會限制根據工作階段的功能。</span><span class="sxs-lookup"><span data-stu-id="46fc4-116">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="46fc4-117">遠端 runspace</span><span class="sxs-lookup"><span data-stu-id="46fc4-117">Remote runspaces</span></span>

<span data-ttu-id="46fc4-118">您現在可以建立 runspace 開啟遠端電腦上，可讓您在遠端電腦上執行命令，並收集在本機的結果。</span><span class="sxs-lookup"><span data-stu-id="46fc4-118">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="46fc4-119">若要建立遠端 runspace，，建立 runspace 時，必須指定遠端連線的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="46fc4-119">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="46fc4-120">請參閱範例 CreateRunspace 和 CreateRunspacePool 方法。</span><span class="sxs-lookup"><span data-stu-id="46fc4-120">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="46fc4-121">RunspaceConnectionInfo 類別所定義的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="46fc4-121">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="46fc4-122">私用 runspace 項目</span><span class="sxs-lookup"><span data-stu-id="46fc4-122">Private runspace elements</span></span>

<span data-ttu-id="46fc4-123">您現在可以建立其項目是公用或私人的 runspace。</span><span class="sxs-lookup"><span data-stu-id="46fc4-123">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="46fc4-124">這可讓您建立其項目可用來在 runspace，但不適用於使用者的 runspace。</span><span class="sxs-lookup"><span data-stu-id="46fc4-124">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="46fc4-125">若要了解 runspace 的哪些項目可以設定為私人 ConstrainedSessionStateEntry 類別，請參閱。</span><span class="sxs-lookup"><span data-stu-id="46fc4-125">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="46fc4-126">執行緒模式和 apartment 狀態的 Runspace</span><span class="sxs-lookup"><span data-stu-id="46fc4-126">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="46fc4-127">您現在可以指定如何建立及使用 runspace 中執行命令時執行緒。</span><span class="sxs-lookup"><span data-stu-id="46fc4-127">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="46fc4-128">請參閱 System.Management.Automation.Runspaces.Runspace.ThreadOptions 和 System.Management.Automation.Runspaces.RunspacePool.ThreadOptions 屬性。</span><span class="sxs-lookup"><span data-stu-id="46fc4-128">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="46fc4-129">您現在可以取得用來在 runspace 中執行命令的執行緒的 apartment 狀態。</span><span class="sxs-lookup"><span data-stu-id="46fc4-129">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="46fc4-130">請參閱 System.Management.Automation.Runspaces.Runspace.ApartmentState 和 System.Management.Automation.Runspaces.RunspacePool.ApartmentState 屬性。</span><span class="sxs-lookup"><span data-stu-id="46fc4-130">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="46fc4-131">交易 cmdlet</span><span class="sxs-lookup"><span data-stu-id="46fc4-131">Transaction cmdlets</span></span>

<span data-ttu-id="46fc4-132">您現在可以建立可在交易內使用的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="46fc4-132">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="46fc4-133">在交易中使用 cmdlet 時，它的動作是暫時性的並可以接受或拒絕的 Windows PowerShell 所提供的交易 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="46fc4-133">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="46fc4-134">如需有關交易的詳細資訊，請參閱如何支援交易。</span><span class="sxs-lookup"><span data-stu-id="46fc4-134">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="46fc4-135">交易的提供者</span><span class="sxs-lookup"><span data-stu-id="46fc4-135">Transaction provider</span></span>

<span data-ttu-id="46fc4-136">您現在可以建立可在交易內使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="46fc4-136">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="46fc4-137">類似於 cmdlet，在交易中使用的提供者時，它的動作是暫時性的並可以接受或拒絕的 Windows PowerShell 所提供的交易 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="46fc4-137">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="46fc4-138">如需指定提供者類別中的交易支援的詳細資訊，請參閱 System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities 屬性。</span><span class="sxs-lookup"><span data-stu-id="46fc4-138">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="46fc4-139">工作 cmdlet</span><span class="sxs-lookup"><span data-stu-id="46fc4-139">Job cmdlets</span></span>

<span data-ttu-id="46fc4-140">您現在可以撰寫可執行其動作，以工作的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="46fc4-140">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="46fc4-141">這些作業會在背景執行，而不與目前的工作階段互動。</span><span class="sxs-lookup"><span data-stu-id="46fc4-141">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="46fc4-142">如需有關 Windows PowerShell 如何支援工作的詳細資訊，請參閱背景工作。</span><span class="sxs-lookup"><span data-stu-id="46fc4-142">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="46fc4-143">Cmdlet 輸出類型</span><span class="sxs-lookup"><span data-stu-id="46fc4-143">Cmdlet output types</span></span>

<span data-ttu-id="46fc4-144">您現在可以指定您的 cmdlet 所傳回宣告 OutputType 屬性，撰寫您的 cmdlet 時.NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="46fc4-144">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="46fc4-145">這可讓其他人決定藉由查看 cmdlet 的 OutputType 屬性由 cmdlet 傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="46fc4-145">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="46fc4-146">事件支援</span><span class="sxs-lookup"><span data-stu-id="46fc4-146">Event support</span></span>

<span data-ttu-id="46fc4-147">您現在可以撰寫 cmdlet 新增及耗用事件。</span><span class="sxs-lookup"><span data-stu-id="46fc4-147">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="46fc4-148">請參閱 PSEvent 類別。</span><span class="sxs-lookup"><span data-stu-id="46fc4-148">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="46fc4-149">Proxy 命令</span><span class="sxs-lookup"><span data-stu-id="46fc4-149">Proxy commands</span></span>

<span data-ttu-id="46fc4-150">您現在可以撰寫 proxy 命令，可用來執行另一個命令。</span><span class="sxs-lookup"><span data-stu-id="46fc4-150">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="46fc4-151">Proxy 命令可讓您控制哪些功能來源指令程式可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="46fc4-151">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="46fc4-152">例如，您可以建立 proxy 命令，移除原始碼命令所提供的參數。</span><span class="sxs-lookup"><span data-stu-id="46fc4-152">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="46fc4-153">請參閱 ProxyCommand 類別。</span><span class="sxs-lookup"><span data-stu-id="46fc4-153">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="46fc4-154">多個選項的提示</span><span class="sxs-lookup"><span data-stu-id="46fc4-154">Multiple choice prompts</span></span>

<span data-ttu-id="46fc4-155">您現在可以撰寫應用程式，可允許使用者選取多個選項的提示。</span><span class="sxs-lookup"><span data-stu-id="46fc4-155">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="46fc4-156">請參閱 IHostUISupportsMultipleChoiceSelection 介面</span><span class="sxs-lookup"><span data-stu-id="46fc4-156">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="46fc4-157">互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="46fc4-157">Interactive sessions</span></span>

<span data-ttu-id="46fc4-158">您現在可以撰寫可以啟動和停止互動式工作階段的遠端電腦上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="46fc4-158">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="46fc4-159">請參閱 IHostSupportsInteractiveSession 介面。</span><span class="sxs-lookup"><span data-stu-id="46fc4-159">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="46fc4-160">提供者的自訂 Cmdlet 說明</span><span class="sxs-lookup"><span data-stu-id="46fc4-160">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="46fc4-161">您現在可以建立自訂提供者 cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="46fc4-161">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="46fc4-162">自訂的 cmdlet 說明主題可闡述 cmdlet 中的提供者路徑和文件特殊功能，包括提供者新增到 cmdlet 的動態參數的運作方式。</span><span class="sxs-lookup"><span data-stu-id="46fc4-162">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>
