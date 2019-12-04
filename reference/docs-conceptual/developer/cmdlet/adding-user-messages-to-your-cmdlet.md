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
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416021"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="25239-102">新增使用者訊息到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="25239-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="25239-103">Cmdlet 可以撰寫數種可由 Windows PowerShell 執行時間向使用者顯示的訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="25239-104">這些訊息包含下列類型：</span><span class="sxs-lookup"><span data-stu-id="25239-104">These messages include the following types:</span></span>

- <span data-ttu-id="25239-105">包含一般使用者資訊的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="25239-106">包含疑難排解資訊的偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="25239-107">包含通知的警告訊息，指出 Cmdlet 即將執行可能會產生非預期結果的作業。</span><span class="sxs-lookup"><span data-stu-id="25239-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="25239-108">進度報表訊息，其中包含在執行需要很長時間的作業時，Cmdlet 已完成多少工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="25239-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="25239-109">您的 Cmdlet 可以寫入的訊息數目，或 Cmdlet 所寫入的訊息類型沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="25239-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="25239-110">每個訊息的撰寫方式是從 Cmdlet 的輸入處理方法中進行特定的呼叫。</span><span class="sxs-lookup"><span data-stu-id="25239-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="25239-111">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="25239-111">Defining the Cmdlet</span></span>

<span data-ttu-id="25239-112">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="25239-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="25239-113">任何類型的 Cmdlet 都可以從其輸入處理方法寫入使用者通知;因此，一般而言，您可以使用指示 Cmdlet 執行之系統修改的任何動詞來命名此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25239-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="25239-114">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="25239-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="25239-115">停止處理器 Cmdlet 是設計來修改系統;因此，.NET 類別的[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)宣告必須包含 `SupportsShouldProcess` 屬性關鍵字，並設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="25239-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="25239-116">下列程式碼是這個停止進程 Cmdlet 類別的定義。</span><span class="sxs-lookup"><span data-stu-id="25239-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="25239-117">如需有關此定義的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="25239-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="25239-118">定義系統修改的參數</span><span class="sxs-lookup"><span data-stu-id="25239-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="25239-119">Stop-Proc Cmdlet 會定義三個參數： `Name`、`Force`和 `PassThru`。</span><span class="sxs-lookup"><span data-stu-id="25239-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="25239-120">如需定義這些參數的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="25239-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="25239-121">以下是 Stop-Proc Cmdlet 的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="25239-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="25239-122">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="25239-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="25239-123">您的 Cmdlet 必須覆寫輸入處理方法，但通常會是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="25239-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="25239-124">這個 Stop-Proc Cmdlet 會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="25239-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="25239-125">在這種停止進程 Cmdlet 的執行過程中，會呼叫來寫入詳細訊息、debug 訊息和警告訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="25239-126">如需有關此方法如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的詳細資訊，請參閱[建立可修改系統](./creating-a-cmdlet-that-modifies-the-system.md)的指令程式（Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="25239-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="25239-127">撰寫詳細訊息</span><span class="sxs-lookup"><span data-stu-id="25239-127">Writing a Verbose Message</span></span>

<span data-ttu-id="25239-128">[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法是用來撰寫與特定錯誤狀況無關的一般使用者層級資訊。</span><span class="sxs-lookup"><span data-stu-id="25239-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="25239-129">然後，系統管理員可以使用該資訊繼續處理其他命令。</span><span class="sxs-lookup"><span data-stu-id="25239-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="25239-130">此外，使用此方法所撰寫的任何資訊都應該視需要當地語系化。</span><span class="sxs-lookup"><span data-stu-id="25239-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="25239-131">下列來自這個 Stop-Proc Cmdlet 的程式碼會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示兩次[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的呼叫，。</span><span class="sxs-lookup"><span data-stu-id="25239-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="25239-132">撰寫 Debug 訊息</span><span class="sxs-lookup"><span data-stu-id="25239-132">Writing a Debug Message</span></span>

<span data-ttu-id="25239-133">[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法是用來撰寫可用於疑難排解 Cmdlet 作業的「偵錯工具」（debug）訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="25239-134">呼叫是從輸入處理方法進行。</span><span class="sxs-lookup"><span data-stu-id="25239-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="25239-135">Windows PowerShell 也會定義同時提供詳細資訊和偵錯工具資訊的 `Debug` 參數。</span><span class="sxs-lookup"><span data-stu-id="25239-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="25239-136">如果您的 Cmdlet 支援此參數，則不需要在呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)的相同程式碼中呼叫 System.web. [WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)..。</span><span class="sxs-lookup"><span data-stu-id="25239-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="25239-137">下列兩個來自 sample WriteDebug 方法的程式碼區段會從 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的覆寫中，顯示對 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法的呼叫。」（來自）。</span><span class="sxs-lookup"><span data-stu-id="25239-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="25239-138">此 debug 訊息會在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)之前立即寫入。</span><span class="sxs-lookup"><span data-stu-id="25239-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="25239-139">此 debug 訊息會在呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)之前立即寫入。</span><span class="sxs-lookup"><span data-stu-id="25239-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="25239-140">Windows PowerShell 會自動將[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)呼叫路由至追蹤基礎結構和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25239-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="25239-141">這可讓方法呼叫追蹤至裝載應用程式、檔案或偵錯工具，而不需要在 Cmdlet 內執行任何額外的開發工作。</span><span class="sxs-lookup"><span data-stu-id="25239-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="25239-142">下列命令列專案會實行追蹤作業。</span><span class="sxs-lookup"><span data-stu-id="25239-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="25239-143">**PS > 追蹤-運算式停止進程-檔案進程 .log-命令停止-進程記事本**</span><span class="sxs-lookup"><span data-stu-id="25239-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="25239-144">撰寫警告訊息</span><span class="sxs-lookup"><span data-stu-id="25239-144">Writing a Warning Message</span></span>

<span data-ttu-id="25239-145">當指令程式即將執行可能會產生非預期結果的作業時（例如，覆寫唯讀檔案），會使用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法來撰寫警告。</span><span class="sxs-lookup"><span data-stu-id="25239-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="25239-146">下列來自範例 Stop-Proc Cmdlet 的程式碼會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示對[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法所做的呼叫，。</span><span class="sxs-lookup"><span data-stu-id="25239-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="25239-147">撰寫進度訊息</span><span class="sxs-lookup"><span data-stu-id="25239-147">Writing a Progress Message</span></span>

<span data-ttu-id="25239-148">當 Cmdlet 作業需要很長的時間才能完成時，會使用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)來寫入進度訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="25239-149">[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)的呼叫會將傳送至裝載應用程式的[Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)物件傳遞給使用者，以供呈現給使用者使用。</span><span class="sxs-lookup"><span data-stu-id="25239-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="25239-150">這個停止進程 Cmdlet 不會包含[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法的呼叫（call）。</span><span class="sxs-lookup"><span data-stu-id="25239-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="25239-151">下列程式碼範例是由嘗試複製專案的 Cmdlet 所撰寫的進度訊息。</span><span class="sxs-lookup"><span data-stu-id="25239-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="25239-152">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="25239-152">Code Sample</span></span>

<span data-ttu-id="25239-153">如需完整C#的範例程式碼，請參閱[StopProcessSample02 範例](./stopprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="25239-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="25239-154">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="25239-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="25239-155">Windows PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="25239-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="25239-156">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="25239-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="25239-157">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="25239-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="25239-158">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="25239-158">Building the Cmdlet</span></span>

<span data-ttu-id="25239-159">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="25239-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="25239-160">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="25239-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="25239-161">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="25239-161">Testing the Cmdlet</span></span>

<span data-ttu-id="25239-162">當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="25239-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="25239-163">讓我們來測試範例的 Stop-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25239-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="25239-164">如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="25239-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="25239-165">下列命令列專案使用停止程式來停止名為 "NOTEPAD" 的進程、提供詳細語音總機，以及列印偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="25239-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="25239-166">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="25239-166">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="25239-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25239-167">See Also</span></span>

[<span data-ttu-id="25239-168">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="25239-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="25239-169">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="25239-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="25239-170">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="25239-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="25239-171">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="25239-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="25239-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="25239-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
