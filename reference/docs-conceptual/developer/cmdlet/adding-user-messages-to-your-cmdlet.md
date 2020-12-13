---
ms.date: 09/13/2016
ms.topic: reference
title: 新增使用者訊息到您的 Cmdlet
description: 新增使用者訊息到您的 Cmdlet
ms.openlocfilehash: de6fcc093af1d01287eed1eb8cc7b81cf5d2fdd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668332"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="1475d-103">新增使用者訊息到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1475d-103">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="1475d-104">Cmdlet 可以撰寫數種可由 Windows PowerShell 執行時間向使用者顯示的訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-104">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="1475d-105">這些訊息包含下列類型：</span><span class="sxs-lookup"><span data-stu-id="1475d-105">These messages include the following types:</span></span>

- <span data-ttu-id="1475d-106">包含一般使用者資訊的詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-106">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="1475d-107">包含疑難排解資訊的訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-107">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="1475d-108">警告訊息，其中包含 Cmdlet 即將執行的作業可能會產生非預期結果的通知。</span><span class="sxs-lookup"><span data-stu-id="1475d-108">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="1475d-109">進度報告訊息，其中包含在執行需要很長時間的作業時，Cmdlet 已完成多少工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1475d-109">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="1475d-110">您的 Cmdlet 可以寫入的訊息數目，或您的 Cmdlet 所寫入的訊息類型沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="1475d-110">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="1475d-111">每個訊息都是藉由在 Cmdlet 的輸入處理方法內進行特定呼叫來撰寫。</span><span class="sxs-lookup"><span data-stu-id="1475d-111">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="1475d-112">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1475d-112">Defining the Cmdlet</span></span>

<span data-ttu-id="1475d-113">Cmdlet 建立的第一個步驟，一律會命名 Cmdlet 並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="1475d-113">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="1475d-114">任何種類的 Cmdlet 都可以從其輸入處理方法寫入使用者通知;因此，一般而言，您可以使用任何指示 Cmdlet 所執行之系統修改的動詞來命名此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1475d-114">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="1475d-115">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞命令名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="1475d-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="1475d-116">Stop-Proc Cmdlet 是設計來修改系統;因此，.NET 類別的 [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 宣告必須包含 `SupportsShouldProcess` attribute 關鍵字，並設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="1475d-116">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="1475d-117">下列程式碼是此 Stop-Proc Cmdlet 類別的定義。</span><span class="sxs-lookup"><span data-stu-id="1475d-117">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="1475d-118">如需有關此定義的詳細資訊，請參閱 [建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="1475d-118">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="1475d-119">定義修改系統的參數</span><span class="sxs-lookup"><span data-stu-id="1475d-119">Defining Parameters for System Modification</span></span>

<span data-ttu-id="1475d-120">Stop-Proc Cmdlet 會定義三個參數： `Name` 、 `Force` 和 `PassThru` 。</span><span class="sxs-lookup"><span data-stu-id="1475d-120">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="1475d-121">如需定義這些參數的詳細資訊，請參閱 [建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="1475d-121">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="1475d-122">以下是 Stop-Proc Cmdlet 的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="1475d-122">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="1475d-123">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="1475d-123">Overriding an Input Processing Method</span></span>

<span data-ttu-id="1475d-124">您的 Cmdlet 必須覆寫輸入處理方法，最常使用的方法就是 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="1475d-124">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="1475d-125">此 Stop-Proc Cmdlet 會覆寫 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="1475d-125">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="1475d-126">在此 Stop-Proc Cmdlet 的執行中，會進行呼叫以寫入詳細訊息、偵錯工具訊息和警告訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-126">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="1475d-127">如需這個方法如何呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的詳細資訊，請參閱 [建立可修改系統的 Cmdlet （可修改系統](./creating-a-cmdlet-that-modifies-the-system.md)）。</span><span class="sxs-lookup"><span data-stu-id="1475d-127">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="1475d-128">寫入詳細資訊訊息</span><span class="sxs-lookup"><span data-stu-id="1475d-128">Writing a Verbose Message</span></span>

<span data-ttu-id="1475d-129">[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法是用來寫入與特定錯誤狀況不相關的一般使用者層級資訊。</span><span class="sxs-lookup"><span data-stu-id="1475d-129">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="1475d-130">系統管理員接著可以使用該資訊繼續處理其他命令。</span><span class="sxs-lookup"><span data-stu-id="1475d-130">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="1475d-131">此外，使用這個方法所撰寫的任何資訊都應該依照需要當地語系化。</span><span class="sxs-lookup"><span data-stu-id="1475d-131">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="1475d-132">此 Stop-Proc Cmdlet 中的下列程式碼會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示兩個[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的呼叫：。</span><span class="sxs-lookup"><span data-stu-id="1475d-132">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="1475d-133">寫入調試訊息</span><span class="sxs-lookup"><span data-stu-id="1475d-133">Writing a Debug Message</span></span>

<span data-ttu-id="1475d-134">[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法是用來撰寫可用於疑難排解 Cmdlet 操作的偵錯工具訊息（debug）。</span><span class="sxs-lookup"><span data-stu-id="1475d-134">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="1475d-135">從輸入處理方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="1475d-135">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="1475d-136">Windows PowerShell 也會定義同時 `Debug` 提供詳細資訊和偵錯工具資訊的參數。</span><span class="sxs-lookup"><span data-stu-id="1475d-136">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="1475d-137">如果您的 Cmdlet 支援此參數，則不需要在呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)的相同程式碼中呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) ，而不需要呼叫。</span><span class="sxs-lookup"><span data-stu-id="1475d-137">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="1475d-138">範例 Stop-Proc Cmdlet 中的下列兩個程式碼區段會顯示[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的呼叫，以進行呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="1475d-138">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="1475d-139">在呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 之前，會立即寫入此偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="1475d-140">在呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 之前，會立即寫入此偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-140">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="1475d-141">Windows PowerShell 會自動將 [WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 呼叫傳送至追蹤基礎結構和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1475d-141">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="1475d-142">這可讓您不需要在 Cmdlet 內執行任何額外的開發工作，即可將方法呼叫追蹤至主控應用程式、檔案或偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1475d-142">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="1475d-143">下列命令列專案會執行追蹤作業。</span><span class="sxs-lookup"><span data-stu-id="1475d-143">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="1475d-144">**PS> 追蹤-運算式停止-進程-檔進程：命令停止-進程記事本**</span><span class="sxs-lookup"><span data-stu-id="1475d-144">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="1475d-145">寫入警告訊息</span><span class="sxs-lookup"><span data-stu-id="1475d-145">Writing a Warning Message</span></span>

<span data-ttu-id="1475d-146">當 Cmdlet 即將執行可能會產生非預期結果的作業（例如，覆寫唯讀檔案）時，會使用 [WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 方法來寫入警告訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-146">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="1475d-147">下列範例中的程式碼 Stop-Proc Cmdlet 會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中，顯示[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法的呼叫程式碼的呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="1475d-147">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="1475d-148">寫入進度訊息</span><span class="sxs-lookup"><span data-stu-id="1475d-148">Writing a Progress Message</span></span>

<span data-ttu-id="1475d-149">當 Cmdlet 作業需要較長的時間才能完成時，會使用 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 來寫入進度訊息。</span><span class="sxs-lookup"><span data-stu-id="1475d-149">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="1475d-150">對 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 的呼叫會傳遞傳送至主控應用程式的 [Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) 物件，以轉譯給使用者的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="1475d-150">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="1475d-151">這個 Stop-Proc Cmdlet 不會包含 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 方法的呼叫，而不包含呼叫。</span><span class="sxs-lookup"><span data-stu-id="1475d-151">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="1475d-152">下列程式碼是嘗試複製專案之 Cmdlet 所寫入的進度訊息範例。</span><span class="sxs-lookup"><span data-stu-id="1475d-152">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="1475d-153">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="1475d-153">Code Sample</span></span>

<span data-ttu-id="1475d-154">如需完整的 c # 範例程式碼，請參閱 [StopProcessSample02 範例](./stopprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="1475d-154">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="1475d-155">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="1475d-155">Define Object Types and Formatting</span></span>

<span data-ttu-id="1475d-156">Windows PowerShell 使用 .NET 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="1475d-156">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="1475d-157">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="1475d-157">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="1475d-158">如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="1475d-158">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="1475d-159">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1475d-159">Building the Cmdlet</span></span>

<span data-ttu-id="1475d-160">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。</span><span class="sxs-lookup"><span data-stu-id="1475d-160">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="1475d-161">如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="1475d-161">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="1475d-162">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1475d-162">Testing the Cmdlet</span></span>

<span data-ttu-id="1475d-163">當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="1475d-163">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="1475d-164">讓我們測試範例 Stop-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1475d-164">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="1475d-165">如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="1475d-165">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="1475d-166">下列命令列專案會使用 Stop-Proc 來停止名為 "NOTEPAD" 的進程、提供詳細語音總機，以及列印偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="1475d-166">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    <span data-ttu-id="1475d-167">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="1475d-167">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1475d-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1475d-168">See Also</span></span>

[<span data-ttu-id="1475d-169">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1475d-169">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="1475d-170">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1475d-170">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="1475d-171">[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1475d-171">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="1475d-172">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1475d-172">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="1475d-173">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1475d-173">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
