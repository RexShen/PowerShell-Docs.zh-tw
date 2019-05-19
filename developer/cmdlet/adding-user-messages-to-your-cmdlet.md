---
title: 將使用者訊息新增至您的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854928"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="2ca3c-102">新增使用者訊息到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2ca3c-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="2ca3c-103">Cmdlet 可以撰寫數種可在 Windows PowerShell 執行階段向使用者顯示的訊息。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="2ca3c-104">這些訊息包括下列類型：</span><span class="sxs-lookup"><span data-stu-id="2ca3c-104">These messages include the following types:</span></span>

- <span data-ttu-id="2ca3c-105">包含使用者的一般資訊的詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="2ca3c-106">偵錯包含疑難排解資訊的訊息。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="2ca3c-107">警告訊息，它包含一則通知，此指令程式即將執行的作業，可以有未預期的結果。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="2ca3c-108">執行時間較長的作業時，已完成進度報表訊息包含多少相關資訊的運作方式的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="2ca3c-109">沒有任何限制，您的 cmdlet 可寫入的訊息數目，或您 cmdlet 會寫入的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="2ca3c-110">每個訊息會寫入藉由從特定呼叫內的輸入處理方法的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="2ca3c-111">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="2ca3c-111">Defining the Cmdlet</span></span>

<span data-ttu-id="2ca3c-112">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="2ca3c-113">任何類型的指令程式可以從其輸入處理方法，寫入使用者通知因此，在一般情況下，您可以命名使用任何指令動詞，指出此 cmdlet 會執行哪些系統修改此指令程式。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="2ca3c-114">如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="2ca3c-115">停止處理序 cmdlet 被設計來修改系統;因此， [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET 類別的宣告必須包含`SupportsShouldProcess`屬性關鍵字，並設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="2ca3c-116">下列程式碼是此停止程序 cmdlet 類別定義。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="2ca3c-117">如需有關此定義的詳細資訊，請參閱[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="2ca3c-118">修改系統定義的參數</span><span class="sxs-lookup"><span data-stu-id="2ca3c-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="2ca3c-119">停止處理序的指令程式會定義三個參數： `Name`， `Force`，和`PassThru`。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="2ca3c-120">如需有關如何定義這些參數的詳細資訊，請參閱 <<c0> [ 建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="2ca3c-121">以下是停止程序 cmdlet 的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="2ca3c-122">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="2ca3c-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="2ca3c-123">您的 cmdlet 必須覆寫輸入處理方法，通常就會[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="2ca3c-124">此處理序停止外 cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="2ca3c-125">在此停止程序 cmdlet 實作中，會呼叫寫入詳細資訊訊息、 偵錯訊息和警告訊息。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="2ca3c-126">如需有關如何呼叫這個方法[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，請參閱[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="2ca3c-127">寫入詳細資訊訊息</span><span class="sxs-lookup"><span data-stu-id="2ca3c-127">Writing a Verbose Message</span></span>

<span data-ttu-id="2ca3c-128">[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法用來撰寫與特定的錯誤情況不相關的一般使用者層級資訊。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="2ca3c-129">系統管理員接著可以使用該資訊以繼續處理其他命令。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="2ca3c-130">此外，視需要應該當地語系化使用這個方法所撰寫的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="2ca3c-131">下列程式碼從這個停止程序的指令程式會顯示兩個呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的覆寫從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="2ca3c-132">撰寫偵錯訊息</span><span class="sxs-lookup"><span data-stu-id="2ca3c-132">Writing a Debug Message</span></span>

<span data-ttu-id="2ca3c-133">[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法用來撰寫可以用來疑難排解 cmdlet 作業的偵錯訊息。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="2ca3c-134">從輸入處理方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="2ca3c-135">Windows PowerShell 也會定義`Debug`參數顯示兩者的詳細資訊，及偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="2ca3c-136">如果您的 cmdlet 會支援這個參數，它不需要呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)在相同的程式碼會呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="2ca3c-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="2ca3c-137">下列兩個範例停止程序 cmdlet 中的程式碼區段會顯示呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的覆寫從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="2ca3c-138">此偵錯訊息寫入之前，立即[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="2ca3c-139">此偵錯訊息寫入之前，立即[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)呼叫。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="2ca3c-140">Windows PowerShell 會自動路由傳送任何[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)呼叫追蹤基礎結構和 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="2ca3c-141">這可讓方法呼叫來追蹤主控應用程式、 檔案，或偵錯工具，而不需要執行此指令程式中任何額外的開發工作。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="2ca3c-142">下列命令列的項目會實作追蹤作業。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="2ca3c-143">**PS > 追蹤運算式停止程序-檔案 proc.log-命令停止程序 [記事本]**</span><span class="sxs-lookup"><span data-stu-id="2ca3c-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="2ca3c-144">寫入一則警告訊息</span><span class="sxs-lookup"><span data-stu-id="2ca3c-144">Writing a Warning Message</span></span>

<span data-ttu-id="2ca3c-145">[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法用來執行的作業可能會有非預期的結果，例如覆寫唯讀檔案，此 cmdlet 時，寫入一個警告。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="2ca3c-146">Cmdlet 範例停止程序的下列程式碼會示範呼叫[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法的覆寫從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="2ca3c-147">寫入進度訊息</span><span class="sxs-lookup"><span data-stu-id="2ca3c-147">Writing a Progress Message</span></span>

<span data-ttu-id="2ca3c-148">[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)用來寫入進度訊息，當 cmdlet 作業會需要更的長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="2ca3c-149">呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)通過[System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)傳送至裝載的應用程式呈現給使用者的物件。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="2ca3c-150">此處理序停止外 cmdlet 不包含呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="2ca3c-151">下列程式碼是由指令程式來嘗試複製項目寫入進度訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="2ca3c-152">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="2ca3c-152">Code Sample</span></span>

<span data-ttu-id="2ca3c-153">完整C#程式碼範例，請參閱 < [StopProcessSample02 範例](./stopprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="2ca3c-154">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="2ca3c-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="2ca3c-155">Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="2ca3c-156">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="2ca3c-157">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="2ca3c-158">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="2ca3c-158">Building the Cmdlet</span></span>

<span data-ttu-id="2ca3c-159">在實作之後的 cmdlet，它必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="2ca3c-160">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="2ca3c-161">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2ca3c-161">Testing the Cmdlet</span></span>

<span data-ttu-id="2ca3c-162">當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="2ca3c-163">我們來測試範例停止程序 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="2ca3c-164">如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="2ca3c-165">下列命令列的項目使用停止程序來停止名為"NOTEPAD"的處理序、 提供詳細的通知，並列印偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="2ca3c-166">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2ca3c-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="2ca3c-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca3c-167">See Also</span></span>

[<span data-ttu-id="2ca3c-168">建立修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2ca3c-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="2ca3c-169">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2ca3c-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="2ca3c-170">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="2ca3c-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="2ca3c-171">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="2ca3c-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2ca3c-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2ca3c-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
