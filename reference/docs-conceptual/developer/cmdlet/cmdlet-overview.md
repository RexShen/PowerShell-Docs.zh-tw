---
title: Cmdlet 總覽 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: 14200aed2fb94c37c8b8af29650f602945e7ac1c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365887"
---
# <a name="cmdlet-overview"></a><span data-ttu-id="53800-102">Cmdlet 概觀</span><span class="sxs-lookup"><span data-stu-id="53800-102">Cmdlet Overview</span></span>

<span data-ttu-id="53800-103">Cmdlet 是在 Windows PowerShell 環境中使用的輕量命令。</span><span class="sxs-lookup"><span data-stu-id="53800-103">A cmdlet is a lightweight command that is used in the Windows PowerShell environment.</span></span> <span data-ttu-id="53800-104">Windows PowerShell 執行時間會在命令列提供的自動化腳本內容中叫用這些 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-104">The Windows PowerShell runtime invokes these cmdlets within the context of automation scripts that are provided at the command line.</span></span> <span data-ttu-id="53800-105">Windows PowerShell 執行時間也會透過 Windows PowerShell Api 以程式設計方式叫用它們。</span><span class="sxs-lookup"><span data-stu-id="53800-105">The Windows PowerShell runtime also invokes them programmatically through Windows PowerShell APIs.</span></span>

## <a name="cmdlets"></a><span data-ttu-id="53800-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="53800-106">Cmdlets</span></span>

<span data-ttu-id="53800-107">Cmdlet 會執行動作，而且通常會將 Microsoft .NET Framework 物件傳回至管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="53800-107">Cmdlets perform an action and typically return a Microsoft .NET Framework object to the next command in the pipeline.</span></span> <span data-ttu-id="53800-108">若要撰寫 Cmdlet，您必須執行一個衍生自兩個特製化 Cmdlet 基類之一的 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="53800-108">To write a cmdlet, you must implement a cmdlet class that derives from one of two specialized cmdlet base classes.</span></span> <span data-ttu-id="53800-109">衍生的類別必須：</span><span class="sxs-lookup"><span data-stu-id="53800-109">The derived class must:</span></span>

- <span data-ttu-id="53800-110">宣告會將衍生類別識別為 Cmdlet 的屬性。</span><span class="sxs-lookup"><span data-stu-id="53800-110">Declare an attribute that identifies the derived class as a cmdlet.</span></span>

- <span data-ttu-id="53800-111">定義使用屬性裝飾的公用屬性，以將公用屬性識別為 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="53800-111">Define public properties that are decorated with attributes that identify the public properties as cmdlet parameters.</span></span>

- <span data-ttu-id="53800-112">覆寫一或多個輸入處理方法來處理記錄。</span><span class="sxs-lookup"><span data-stu-id="53800-112">Override one or more of the input processing methods to process records.</span></span>

<span data-ttu-id="53800-113">您可以使用[import-module](/powershell/module/microsoft.powershell.core/import-module) Cmdlet 直接載入包含類別的元件，也可以使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API 來建立裝載元件的主應用程式，以載入該元件。</span><span class="sxs-lookup"><span data-stu-id="53800-113">You can load the assembly that contains the class directly by using the [Import-Module](/powershell/module/microsoft.powershell.core/import-module) cmdlet, or you can create a host application that loads the assembly by using the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API.</span></span> <span data-ttu-id="53800-114">這兩種方法都可讓您以程式設計方式和命令列存取 Cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="53800-114">Both methods provide programmatic and command-line access to the functionality of the cmdlet.</span></span>

## <a name="cmdlet-terms"></a><span data-ttu-id="53800-115">Cmdlet 詞彙</span><span class="sxs-lookup"><span data-stu-id="53800-115">Cmdlet Terms</span></span>

<span data-ttu-id="53800-116">以下是 Windows PowerShell Cmdlet 檔中經常使用的詞彙：</span><span class="sxs-lookup"><span data-stu-id="53800-116">The following terms are used frequently in the Windows PowerShell cmdlet documentation:</span></span>

### <a name="cmdlet-attribute"></a><span data-ttu-id="53800-117">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="53800-117">Cmdlet attribute</span></span>

<span data-ttu-id="53800-118">用來將 Cmdlet 類別宣告為 Cmdlet 的 .NET Framework 屬性。</span><span class="sxs-lookup"><span data-stu-id="53800-118">A .NET Framework attribute that is used to declare a cmdlet class as a cmdlet.</span></span>
<span data-ttu-id="53800-119">雖然 PowerShell 使用其他幾個選擇性的屬性，但 Cmdlet 屬性是必要的。</span><span class="sxs-lookup"><span data-stu-id="53800-119">Although PowerShell uses several other attributes that are optional, the Cmdlet attribute is required.</span></span>
<span data-ttu-id="53800-120">如需此屬性的詳細資訊，請參閱[Cmdlet 屬性](cmdlet-attribute-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="53800-120">For more information about this attribute, see [Cmdlet Attribute Declaration](cmdlet-attribute-declaration.md).</span></span>

### <a name="cmdlet-parameter"></a><span data-ttu-id="53800-121">指令程式參數</span><span class="sxs-lookup"><span data-stu-id="53800-121">Cmdlet parameter</span></span>

<span data-ttu-id="53800-122">公用屬性，定義可供使用者或執行 Cmdlet 之應用程式使用的參數。</span><span class="sxs-lookup"><span data-stu-id="53800-122">The public properties that define the parameters that are available to the user or to the application that is running the cmdlet.</span></span>
<span data-ttu-id="53800-123">Cmdlet 可以有必要、命名、位置和*切換*參數。</span><span class="sxs-lookup"><span data-stu-id="53800-123">Cmdlets can have required, named, positional, and *switch* parameters.</span></span>
<span data-ttu-id="53800-124">切換參數可讓您定義只有在呼叫中指定參數時才會評估的參數。</span><span class="sxs-lookup"><span data-stu-id="53800-124">Switch parameters allow you to define parameters that are evaluated only if the parameters are specified in the call.</span></span>
<span data-ttu-id="53800-125">如需不同類型參數的詳細資訊，請參閱[Cmdlet 參數](cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-125">For more information about the different types of parameters, see [Cmdlet Parameters](cmdlet-parameters.md).</span></span>

### <a name="parameter-set"></a><span data-ttu-id="53800-126">參數集</span><span class="sxs-lookup"><span data-stu-id="53800-126">Parameter set</span></span>

<span data-ttu-id="53800-127">可在相同命令中用來執行特定動作的一組參數。</span><span class="sxs-lookup"><span data-stu-id="53800-127">A group of parameters that can be used in the same command to perform a specific action.</span></span>
<span data-ttu-id="53800-128">一個 Cmdlet 可以有多個參數集，但每個參數集必須至少有一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="53800-128">A cmdlet can have multiple parameter sets, but each parameter set must have at least one parameter that is unique.</span></span>
<span data-ttu-id="53800-129">良好的 Cmdlet 設計強烈建議，unique 參數也是必要參數。</span><span class="sxs-lookup"><span data-stu-id="53800-129">Good cmdlet design strongly suggests that the unique parameter also be a required parameter.</span></span>
<span data-ttu-id="53800-130">如需參數集的詳細資訊，請參閱[Cmdlet 參數集](cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-130">For more information about parameter sets, see [Cmdlet Parameter Sets](cmdlet-parameter-sets.md).</span></span>

### <a name="dynamic-parameter"></a><span data-ttu-id="53800-131">動態參數</span><span class="sxs-lookup"><span data-stu-id="53800-131">Dynamic parameter</span></span>

<span data-ttu-id="53800-132">在執行時間新增至 Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="53800-132">A parameter that is added to the cmdlet at runtime.</span></span>
<span data-ttu-id="53800-133">一般而言，當另一個參數設定為特定值時，會將動態參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-133">Typically, the dynamic parameters are added to the cmdlet when another parameter is set to a specific value.</span></span>
<span data-ttu-id="53800-134">如需動態參數的詳細資訊，請參閱[Cmdlet 動態參數](cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-134">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](cmdlet-dynamic-parameters.md).</span></span>

### <a name="input-processing-method"></a><span data-ttu-id="53800-135">輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="53800-135">Input processing method</span></span>

<span data-ttu-id="53800-136">Cmdlet 可用來處理接收為輸入之記錄的方法。</span><span class="sxs-lookup"><span data-stu-id="53800-136">A method that a cmdlet can use to process the records it receives as input.</span></span>
<span data-ttu-id="53800-137">輸入處理方法包括 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 方法（ProcessRecord 方法），也就是 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) [System.Management.Automation.Cmdlet.EndProcessing（系統管理元件）。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) 方法，並將其與系統管理元件進行比對。</span><span class="sxs-lookup"><span data-stu-id="53800-137">The input processing methods include the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, and the [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) method.</span></span> <span data-ttu-id="53800-138">當您執行 Cmdlet 時，您必須至少覆寫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)、和的其中一項，並[加以取代。System.servicemodel 方法...](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="53800-138">When you implement a cmdlet, you must override at least one of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) methods.</span></span>
<span data-ttu-id="53800-139">一般來說， [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是您覆寫的方法，因為它會針對 Cmdlet 所處理的每一筆記錄進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="53800-139">Typically, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is the method that you override because it is called for every record that the cmdlet processes.</span></span>
<span data-ttu-id="53800-140">相反地，會呼叫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法和[system.string 方法一](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)次，以執行記錄的前置處理或後置處理，而不需要進行此工作。</span><span class="sxs-lookup"><span data-stu-id="53800-140">In contrast, the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method are called one time to perform pre-processing or post-processing of the records.</span></span>
<span data-ttu-id="53800-141">如需這些方法的詳細資訊，請參閱[輸入處理方法](cmdlet-input-processing-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-141">For more information about these methods, see [Input Processing Methods](cmdlet-input-processing-methods.md).</span></span>

### <a name="shouldprocess-feature"></a><span data-ttu-id="53800-142">ShouldProcess 功能</span><span class="sxs-lookup"><span data-stu-id="53800-142">ShouldProcess feature</span></span>

<span data-ttu-id="53800-143">PowerShell 可讓您建立 Cmdlet，在 Cmdlet 對系統進行變更之前提示使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="53800-143">PowerShell allows you to create cmdlets that prompt the user for feedback before the cmdlet makes a change to the system.</span></span>
<span data-ttu-id="53800-144">若要使用這項功能，Cmdlet 必須在宣告 Cmdlet 屬性時宣告它支援 ShouldProcess 功能，而且 Cmdlet 必須呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)在輸入處理方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="53800-144">To use this feature, the cmdlet must declare that it supports the ShouldProcess feature when you declare the Cmdlet attribute, and the cmdlet must call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods from within an input processing method.</span></span>
<span data-ttu-id="53800-145">如需如何支援 ShouldProcess 功能的詳細資訊，請參閱[要求確認](requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-145">For more information about how to support the ShouldProcess functionality, see [Requesting Confirmation](requesting-confirmation-from-cmdlets.md).</span></span>

### <a name="transaction"></a><span data-ttu-id="53800-146">Transaction</span><span class="sxs-lookup"><span data-stu-id="53800-146">Transaction</span></span>

<span data-ttu-id="53800-147">視為單一工作的命令邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="53800-147">A logical group of commands that are treated as a single task.</span></span>
<span data-ttu-id="53800-148">如果群組中有任何命令失敗，此工作會自動失敗，而且使用者可以選擇接受或拒絕在交易內執行的動作。</span><span class="sxs-lookup"><span data-stu-id="53800-148">The task automatically fails if any command in the group fails, and the user has the choice to accept or reject the actions performed within the transaction.</span></span>
<span data-ttu-id="53800-149">若要參與交易，Cmdlet 必須在宣告 Cmdlet 屬性時宣告它支援交易。</span><span class="sxs-lookup"><span data-stu-id="53800-149">To participate in a transaction, the cmdlet must declare that it supports transactions when the Cmdlet attribute is declared.</span></span>
<span data-ttu-id="53800-150">對交易的支援是在 Windows PowerShell 2.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="53800-150">Support for transactions was introduced in Windows PowerShell 2.0.</span></span>
<span data-ttu-id="53800-151">如需交易的詳細資訊，請參閱[如何支援交易](how-to-support-transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-151">For more information about transactions, see [How to Support Transactions](how-to-support-transactions.md).</span></span>

## <a name="how-cmdlets-differ-from-commands"></a><span data-ttu-id="53800-152">Cmdlet 與命令有何不同</span><span class="sxs-lookup"><span data-stu-id="53800-152">How Cmdlets Differ from Commands</span></span>

<span data-ttu-id="53800-153">Cmdlet 與其他命令 shell 環境中的命令不同，有下列幾種方式：</span><span class="sxs-lookup"><span data-stu-id="53800-153">Cmdlets differ from commands in other command-shell environments in the following ways:</span></span>

- <span data-ttu-id="53800-154">Cmdlet 是 .NET Framework 類別的實例;它們不是獨立的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="53800-154">Cmdlets are instances of .NET Framework classes; they are not stand-alone executables.</span></span>

- <span data-ttu-id="53800-155">您可以從短短幾行程式碼建立 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-155">Cmdlets can be created from as few as a dozen lines of code.</span></span>

- <span data-ttu-id="53800-156">Cmdlet 通常不會執行自己的剖析、錯誤簡報或輸出格式。</span><span class="sxs-lookup"><span data-stu-id="53800-156">Cmdlets do not generally do their own parsing, error presentation, or output formatting.</span></span> <span data-ttu-id="53800-157">剖析、錯誤簡報和輸出格式是由 Windows PowerShell 執行時間處理。</span><span class="sxs-lookup"><span data-stu-id="53800-157">Parsing, error presentation, and output formatting are handled by the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="53800-158">Cmdlet 會處理來自管線的輸入物件，而不是從文字的資料流程，而 Cmdlet 通常會將物件當做輸出傳遞至管線。</span><span class="sxs-lookup"><span data-stu-id="53800-158">Cmdlets process input objects from the pipeline rather than from streams of text, and cmdlets typically deliver objects as output to the pipeline.</span></span>

- <span data-ttu-id="53800-159">Cmdlet 是記錄導向的，因為它們會一次處理一個物件。</span><span class="sxs-lookup"><span data-stu-id="53800-159">Cmdlets are record-oriented because they process a single object at a time.</span></span>

## <a name="cmdlet-base-classes"></a><span data-ttu-id="53800-160">Cmdlet 基類</span><span class="sxs-lookup"><span data-stu-id="53800-160">Cmdlet Base Classes</span></span>

<span data-ttu-id="53800-161">Windows PowerShell 支援衍生自下列兩個基類的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-161">Windows PowerShell supports cmdlets that are derived from the following two base classes.</span></span>

- <span data-ttu-id="53800-162">大部分的 Cmdlet 都是以衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)基類的 .NET Framework 類別為基礎。</span><span class="sxs-lookup"><span data-stu-id="53800-162">Most cmdlets are based on .NET Framework classes that derive from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span> <span data-ttu-id="53800-163">衍生自這個類別可讓 Cmdlet 使用 Windows PowerShell 執行時間上的最小相依性集合。</span><span class="sxs-lookup"><span data-stu-id="53800-163">Deriving from this class allows a cmdlet to use the minimum set of dependencies on the Windows PowerShell runtime.</span></span> <span data-ttu-id="53800-164">這有兩個優點。</span><span class="sxs-lookup"><span data-stu-id="53800-164">This has two benefits.</span></span> <span data-ttu-id="53800-165">第一個優點是 Cmdlet 物件較小，而且您較不可能受到 Windows PowerShell 執行時間變更的影響。</span><span class="sxs-lookup"><span data-stu-id="53800-165">The first benefit is that the cmdlet objects are smaller, and you are less likely to be affected by changes to the Windows PowerShell runtime.</span></span> <span data-ttu-id="53800-166">第二個優點是，如果您需要，可以直接建立 Cmdlet 物件的實例，然後直接叫用它，而不是透過 Windows PowerShell 執行時間叫用它。</span><span class="sxs-lookup"><span data-stu-id="53800-166">The second benefit is that, if you have to, you can directly create an instance of the cmdlet object and then invoke it directly instead of invoking it through the Windows PowerShell runtime.</span></span>

- <span data-ttu-id="53800-167">較複雜的 Cmdlet 是以衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基類的 .NET Framework 類別為基礎。</span><span class="sxs-lookup"><span data-stu-id="53800-167">The more-complex cmdlets are based on .NET Framework classes that derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="53800-168">衍生自這個類別可讓您更容易存取 Windows PowerShell 執行時間。</span><span class="sxs-lookup"><span data-stu-id="53800-168">Deriving from this class gives you much more access to the Windows PowerShell runtime.</span></span> <span data-ttu-id="53800-169">此存取可讓您的 Cmdlet 呼叫腳本、存取提供者，以及存取目前的會話狀態。</span><span class="sxs-lookup"><span data-stu-id="53800-169">This access allows your cmdlet to call scripts, to access providers, and to access the current session state.</span></span> <span data-ttu-id="53800-170">（若要存取目前的會話狀態，您可以取得並設定會話變數和喜好設定）。不過，衍生自這個類別會增加 Cmdlet 物件的大小，這表示您的 Cmdlet 會與目前的 Windows PowerShell 執行時間版本緊密結合。</span><span class="sxs-lookup"><span data-stu-id="53800-170">(To access the current session state, you get and set session variables and preferences.) However, deriving from this class increases the size of the cmdlet object, and it means that your cmdlet is more tightly coupled to the current version of the Windows PowerShell runtime.</span></span>

<span data-ttu-id="53800-171">一般而言，除非您需要 Windows PowerShell 執行時間的延伸存取權，否則您應該衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="53800-171">In general, unless you need the extended access to the Windows PowerShell runtime, you should derive from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="53800-172">不過，Windows PowerShell 執行時間有廣泛的記錄功能，可執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-172">However, the Windows PowerShell runtime has extensive logging capabilities for the execution of cmdlets.</span></span> <span data-ttu-id="53800-173">如果您的審核模型相依于此記錄，您可以藉由衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別，防止從另一個 Cmdlet 中執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-173">If your auditing model depends on this logging, you can prevent the execution of your cmdlet from within another cmdlet by deriving from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="input-processing-methods"></a><span data-ttu-id="53800-174">輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="53800-174">Input Processing Methods</span></span>

<span data-ttu-id="53800-175">[System.web](/dotnet/api/System.Management.Automation.Cmdlet)類別提供了下列用來處理記錄的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="53800-175">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides the following virtual methods that are used to process records.</span></span> <span data-ttu-id="53800-176">所有衍生的 Cmdlet 類別都必須覆寫前三個方法的其中一個或多個：</span><span class="sxs-lookup"><span data-stu-id="53800-176">All the derived cmdlet classes must override one or more of the first three methods:</span></span>

- <span data-ttu-id="53800-177">， [BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)：。用來為 Cmdlet 提供選擇性的一次性預先處理功能。</span><span class="sxs-lookup"><span data-stu-id="53800-177">[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing): Used to provide optional one-time, pre-processing functionality for the cmdlet.</span></span>

- <span data-ttu-id="53800-178">， [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)：。用來提供 Cmdlet 的記錄逐記錄處理功能。</span><span class="sxs-lookup"><span data-stu-id="53800-178">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord): Used to provide record-by-record processing functionality for the cmdlet.</span></span> <span data-ttu-id="53800-179">視 Cmdlet 的輸入而定，可能會呼叫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法任意次數，或根本不需要任何次數。</span><span class="sxs-lookup"><span data-stu-id="53800-179">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method might be called any number of times, or not at all, depending on the input of the cmdlet.</span></span>

- <span data-ttu-id="53800-180">System.servicemodel. [Cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)：用來為 Cmdlet 提供選擇性的一次性、後置處理功能。</span><span class="sxs-lookup"><span data-stu-id="53800-180">[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing): Used to provide optional one-time, post-processing functionality for the cmdlet.</span></span>

- <span data-ttu-id="53800-181">， [StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)：。用來在使用者以非同步方式停止 Cmdlet 時停止處理（例如，按下 CTRL + C）。</span><span class="sxs-lookup"><span data-stu-id="53800-181">[System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing): Used to stop processing when the user stops the cmdlet asynchronously (for example,  by pressing CTRL+C).</span></span>

<span data-ttu-id="53800-182">如需這些方法的詳細資訊，請參閱[Cmdlet 輸入處理方法](./cmdlet-input-processing-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-182">For more information about these methods, see [Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md).</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="53800-183">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="53800-183">Cmdlet Attributes</span></span>

<span data-ttu-id="53800-184">Windows PowerShell 定義數個用來管理 Cmdlet 的 .NET Framework 屬性，並指定 Windows PowerShell 所提供且可能由指令程式所要求的一般功能。</span><span class="sxs-lookup"><span data-stu-id="53800-184">Windows PowerShell defines several .NET Framework attributes that are used to manage cmdlets and to specify common functionality that is provided by Windows PowerShell and that might be required by the cmdlet.</span></span> <span data-ttu-id="53800-185">例如，屬性是用來指定類別做為 Cmdlet、指定 Cmdlet 的參數，以及要求輸入的驗證，讓 Cmdlet 開發人員不需要在其 Cmdlet 程式碼中執行該功能。</span><span class="sxs-lookup"><span data-stu-id="53800-185">For example, attributes are used to designate a class as a cmdlet, to specify the parameters of the cmdlet, and to request the validation of input so that cmdlet developers do not have to implement that functionality in their cmdlet code.</span></span> <span data-ttu-id="53800-186">如需有關屬性的詳細資訊，請參閱[Windows PowerShell 屬性](./cmdlet-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-186">For more information about attributes, see [Windows PowerShell Attributes](./cmdlet-attributes.md).</span></span>

## <a name="cmdlet-names"></a><span data-ttu-id="53800-187">Cmdlet 名稱</span><span class="sxs-lookup"><span data-stu-id="53800-187">Cmdlet Names</span></span>

<span data-ttu-id="53800-188">Windows PowerShell 會使用動詞和名詞名稱配對來命名 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-188">Windows PowerShell uses a verb-and-noun name pair to name cmdlets.</span></span> <span data-ttu-id="53800-189">例如，Windows PowerShell 中包含的 `Get-Command` Cmdlet 是用來取得在命令 shell 中註冊的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53800-189">For example, the `Get-Command` cmdlet included in Windows PowerShell is used to get all the cmdlets that are registered in the command shell.</span></span> <span data-ttu-id="53800-190">動詞識別指令程式所執行的動作，名詞則識別此 Cmdlet 執行其動作的資源。</span><span class="sxs-lookup"><span data-stu-id="53800-190">The verb identifies the action that the cmdlet performs, and the noun identifies the resource on which the cmdlet performs its action.</span></span>

<span data-ttu-id="53800-191">當 .NET Framework 類別宣告為 Cmdlet 時，會指定這些名稱。</span><span class="sxs-lookup"><span data-stu-id="53800-191">These names are specified when the .NET Framework class is declared as a cmdlet.</span></span> <span data-ttu-id="53800-192">如需如何將 .NET Framework 類別宣告為 Cmdlet 的詳細資訊，請參閱[Cmdlet 屬性](./cmdlet-class-declaration.md)宣告。</span><span class="sxs-lookup"><span data-stu-id="53800-192">For more information about how to declare a .NET Framework class as a cmdlet, see [Cmdlet Attribute Declaration](./cmdlet-class-declaration.md).</span></span>

## <a name="writing-cmdlet-code"></a><span data-ttu-id="53800-193">撰寫 Cmdlet 程式碼</span><span class="sxs-lookup"><span data-stu-id="53800-193">Writing Cmdlet Code</span></span>

<span data-ttu-id="53800-194">本檔提供兩種方式來探索 Cmdlet 程式碼的撰寫方式。</span><span class="sxs-lookup"><span data-stu-id="53800-194">This document provides two ways to discover how cmdlet code is written.</span></span> <span data-ttu-id="53800-195">如果您想要查看程式碼而不會有太多說明，請參閱[Cmdlet 程式碼的範例](./examples-of-cmdlet-code.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-195">If you prefer to see the code without much explanation, see [Examples of Cmdlet Code](./examples-of-cmdlet-code.md).</span></span> <span data-ttu-id="53800-196">如果您想要更多有關程式碼的說明，請參閱[GetProc 教學](./getproc-tutorial.md)課程、 [StopProc 教學](./stopproc-tutorial.md)課程或[SelectStr 教學](./selectstr-tutorial.md)課程主題。</span><span class="sxs-lookup"><span data-stu-id="53800-196">If you prefer more explanation about the code, see the [GetProc Tutorial](./getproc-tutorial.md),  [StopProc Tutorial](./stopproc-tutorial.md), or [SelectStr Tutorial](./selectstr-tutorial.md) topics.</span></span>

<span data-ttu-id="53800-197">如需撰寫 Cmdlet 之指導方針的詳細資訊，請參閱[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="53800-197">For more information about the guidelines for writing cmdlets, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53800-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53800-198">See Also</span></span>

[<span data-ttu-id="53800-199">Windows PowerShell Cmdlet 概念</span><span class="sxs-lookup"><span data-stu-id="53800-199">Windows PowerShell Cmdlet Concepts</span></span>](./windows-powershell-cmdlet-concepts.md)

[<span data-ttu-id="53800-200">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="53800-200">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="53800-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="53800-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
