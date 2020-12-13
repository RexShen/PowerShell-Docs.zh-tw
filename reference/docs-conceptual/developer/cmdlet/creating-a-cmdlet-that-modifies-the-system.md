---
ms.date: 09/13/2016
ms.topic: reference
title: 建立可修改系統的 Cmdlet
description: 建立可修改系統的 Cmdlet
ms.openlocfilehash: 757f2c97bb4b5dcf2fb633cd35fe52bc5f6c5cf9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355539"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="7db53-103">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7db53-103">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="7db53-104">有時 Cmdlet 必須修改系統的執行狀態，而不只是 Windows PowerShell 執行時間的狀態。</span><span class="sxs-lookup"><span data-stu-id="7db53-104">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="7db53-105">在這些情況下，Cmdlet 應可讓使用者有機會確認是否要進行變更。</span><span class="sxs-lookup"><span data-stu-id="7db53-105">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="7db53-106">若要支援確認，Cmdlet 必須做兩件事。</span><span class="sxs-lookup"><span data-stu-id="7db53-106">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="7db53-107">宣告當您藉由將 SupportsShouldProcess 關鍵字設定為來指定 [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 屬性時，此 Cmdlet 支援 `true` 確認。</span><span class="sxs-lookup"><span data-stu-id="7db53-107">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="7db53-108">在 (指令程式執行期間呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ，如下列範例所示) 。</span><span class="sxs-lookup"><span data-stu-id="7db53-108">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="7db53-109">藉由支援確認，指令程式 `Confirm` 會公開 `WhatIf` Windows PowerShell 提供的和參數，也符合 Cmdlet 的開發指導方針 (如需 Cmdlet 開發指導方針的詳細資訊，請參閱 [Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)。 ) 。</span><span class="sxs-lookup"><span data-stu-id="7db53-109">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="7db53-110">變更系統</span><span class="sxs-lookup"><span data-stu-id="7db53-110">Changing the System</span></span>

<span data-ttu-id="7db53-111">「變更系統」的動作是指任何可能會在 Windows PowerShell 之外變更系統狀態的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7db53-111">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="7db53-112">例如，停止進程、啟用或停用使用者帳戶，或將資料列加入至資料庫資料表，就會對應該確認的系統進行變更。</span><span class="sxs-lookup"><span data-stu-id="7db53-112">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span>
<span data-ttu-id="7db53-113">相反地，讀取資料或建立暫時性連接的作業不會變更系統，通常不需要確認。</span><span class="sxs-lookup"><span data-stu-id="7db53-113">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="7db53-114">如果動作的效果限制在 Windows PowerShell 執行時間內（例如），則也不需要確認 `set-variable` 。</span><span class="sxs-lookup"><span data-stu-id="7db53-114">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="7db53-115">可能或可能不會進行持續變更的 Cmdlet 只有在 `SupportsShouldProcess` 即將進行持續變更時，才會宣告和呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 。</span><span class="sxs-lookup"><span data-stu-id="7db53-115">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="7db53-116">ShouldProcess 確認只適用于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7db53-116">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="7db53-117">如果命令或腳本藉由直接呼叫 .NET 方法或屬性來修改系統的執行狀態，或呼叫 Windows PowerShell 之外的應用程式，則無法使用這種形式的確認。</span><span class="sxs-lookup"><span data-stu-id="7db53-117">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="7db53-118">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7db53-118">The StopProc Cmdlet</span></span>

<span data-ttu-id="7db53-119">本主題說明 Stop-Proc Cmdlet，它會嘗試停止使用 Get-Proc Cmdlet 抓取的處理常式 () [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="7db53-119">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="7db53-120">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7db53-120">Defining the Cmdlet</span></span>

<span data-ttu-id="7db53-121">Cmdlet 建立的第一個步驟，一律會命名 Cmdlet 並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="7db53-121">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="7db53-122">因為您要撰寫 Cmdlet 來變更系統，所以應該據此命名。</span><span class="sxs-lookup"><span data-stu-id="7db53-122">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="7db53-123">此 Cmdlet 會停止系統進程，因此此處選擇的動詞名稱為 "Stop"，由 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 類別定義，並以名詞 "Proc" 表示此 Cmdlet 會停止處理常式。</span><span class="sxs-lookup"><span data-stu-id="7db53-123">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="7db53-124">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞命令名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="7db53-124">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="7db53-125">以下是此 Stop-Proc Cmdlet 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="7db53-125">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="7db53-126">請注意，在 [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 宣告中， `SupportsShouldProcess` 屬性關鍵字會設定為，讓指令程式 `true` 能夠呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 ShouldContinue........ [.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="7db53-126">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="7db53-127">若未設定此關鍵字， `Confirm` `WhatIf` 使用者將無法使用和參數。</span><span class="sxs-lookup"><span data-stu-id="7db53-127">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="7db53-128">極具破壞性的動作</span><span class="sxs-lookup"><span data-stu-id="7db53-128">Extremely Destructive Actions</span></span>

<span data-ttu-id="7db53-129">某些作業的破壞性極為嚴重，例如重新格式化使用中的硬碟磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="7db53-129">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="7db53-130">在這些情況下，Cmdlet 應該 `ConfirmImpact`  =  `ConfirmImpact.High` 在宣告[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性時設定。</span><span class="sxs-lookup"><span data-stu-id="7db53-130">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="7db53-131">此設定會強制 Cmdlet 要求使用者確認，即使使用者尚未指定 `Confirm` 參數。</span><span class="sxs-lookup"><span data-stu-id="7db53-131">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="7db53-132">不過，Cmdlet 開發人員應該避免過度使用 `ConfirmImpact` 只是可能破壞性的作業，例如刪除使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="7db53-132">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="7db53-133">請記住，如果 `ConfirmImpact` 設定為[ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) 
 **High**。</span><span class="sxs-lookup"><span data-stu-id="7db53-133">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact)
**High**.</span></span>

<span data-ttu-id="7db53-134">同樣地，某些作業不太可能成為破壞性，雖然它們理論上會修改 Windows PowerShell 外部系統的執行中狀態。</span><span class="sxs-lookup"><span data-stu-id="7db53-134">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="7db53-135">這類 Cmdlet 可以設定 `ConfirmImpact` 為[Confirmimpact。](/dotnet/api/system.management.automation.confirmimpact)</span><span class="sxs-lookup"><span data-stu-id="7db53-135">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact).</span></span>
<span data-ttu-id="7db53-136">這會略過使用者要求只確認中度影響和高影響作業的確認要求。</span><span class="sxs-lookup"><span data-stu-id="7db53-136">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="7db53-137">定義修改系統的參數</span><span class="sxs-lookup"><span data-stu-id="7db53-137">Defining Parameters for System Modification</span></span>

<span data-ttu-id="7db53-138">本節說明如何定義 Cmdlet 參數，包括支援系統修改所需的參數。</span><span class="sxs-lookup"><span data-stu-id="7db53-138">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="7db53-139">如果您需要定義參數的一般資訊，請參閱 [新增處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md) 。</span><span class="sxs-lookup"><span data-stu-id="7db53-139">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="7db53-140">Stop-Proc Cmdlet 會定義三個參數： `Name` 、 `Force` 和 `PassThru` 。</span><span class="sxs-lookup"><span data-stu-id="7db53-140">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="7db53-141">`Name`參數會對應至 `Name` 處理常式輸入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="7db53-141">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="7db53-142">請注意， `Name` 此範例中的參數是必要的，因為如果 Cmdlet 沒有已命名的進程可停止，則此 Cmdlet 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="7db53-142">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="7db53-143">此 `Force` 參數可讓使用者覆寫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7db53-143">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="7db53-144">事實上，任何呼叫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的 Cmdlet 都應該有 `Force` 參數，如此一來，當您 `Force` 指定時，此 Cmdlet 就會略過 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的呼叫，並繼續進行操作。</span><span class="sxs-lookup"><span data-stu-id="7db53-144">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="7db53-145">請注意，這不會影響 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7db53-145">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="7db53-146">`PassThru`此參數可讓使用者指出 Cmdlet 是否透過管線傳遞輸出物件，在此情況下，會在進程停止之後進行。</span><span class="sxs-lookup"><span data-stu-id="7db53-146">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="7db53-147">請注意，此參數會系結至 Cmdlet 本身，而非輸入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="7db53-147">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="7db53-148">以下是 Stop-Proc Cmdlet 的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="7db53-148">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="7db53-149">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="7db53-149">Overriding an Input Processing Method</span></span>

<span data-ttu-id="7db53-150">Cmdlet 必須覆寫輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="7db53-150">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="7db53-151">下列程式碼說明範例 Stop-Proc Cmdlet 中所使用的 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 覆寫。</span><span class="sxs-lookup"><span data-stu-id="7db53-151">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="7db53-152">針對每個要求的處理常式名稱，這個方法可確保進程不是特殊的進程、嘗試停止進程，然後在指定參數時傳送輸出物件 `PassThru` 。</span><span class="sxs-lookup"><span data-stu-id="7db53-152">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="7db53-153">呼叫 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="7db53-153">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="7db53-154">您的 Cmdlet 的輸入處理方法應該呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法，以在 (變更之前確認作業的執行，例如，刪除) 的檔案是對系統執行中的狀態。</span><span class="sxs-lookup"><span data-stu-id="7db53-154">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="7db53-155">這可讓 Windows PowerShell 執行時間在 shell 內提供正確的 "WhatIf" 和 "Confirm" 行為。</span><span class="sxs-lookup"><span data-stu-id="7db53-155">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="7db53-156">如果 Cmdlet 指出它所支援的應該要處理且無法進行 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫，使用者可能會意外修改系統。</span><span class="sxs-lookup"><span data-stu-id="7db53-156">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="7db53-157">呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 時，會將要變更的資源名稱傳送給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定要向使用者顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="7db53-157">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="7db53-158">下列範例會顯示 ShouldProcess 從範例 Stop-Proc Cmdlet 中[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫，以進行[](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的呼叫程式中的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7db53-158">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="7db53-159">呼叫 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="7db53-159">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="7db53-160">對 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的呼叫會將次要訊息傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="7db53-160">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="7db53-161">呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 之後，會傳回 `true` ，而且如果 `Force` 參數未設定為，則會進行此 `true` 呼叫。</span><span class="sxs-lookup"><span data-stu-id="7db53-161">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="7db53-162">然後，使用者可以提供意見反應，以指出作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="7db53-162">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="7db53-163">您的 Cmdlet 會呼叫 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 做為額外的檢查，以檢查是否有潛在危險的系統修改，或當您想要為使用者提供「全部」和「無」選項時。</span><span class="sxs-lookup"><span data-stu-id="7db53-163">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="7db53-164">下列範例會顯示 ShouldContinue 從範例 Stop-Proc Cmdlet 中[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫，以進行[](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫程式中的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7db53-164">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="7db53-165">停止輸入處理</span><span class="sxs-lookup"><span data-stu-id="7db53-165">Stopping Input Processing</span></span>

<span data-ttu-id="7db53-166">進行系統修改之 Cmdlet 的輸入處理方法，必須提供停止處理輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="7db53-166">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="7db53-167">在這個 Stop-Proc 指令程式的情況下，會從 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法到 system.string [\*](/dotnet/api/System.Diagnostics.Process.Kill) 方法的呼叫，進行呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="7db53-167">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="7db53-168">因為 `PassThru` 參數是設定為 `true` ，所以 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 也會呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) ，以將處理常式物件傳送至管線的進程中。</span><span class="sxs-lookup"><span data-stu-id="7db53-168">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7db53-169">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7db53-169">Code Sample</span></span>

<span data-ttu-id="7db53-170">如需完整的 c # 範例程式碼，請參閱 [StopProcessSample01 範例](./stopprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="7db53-170">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="7db53-171">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="7db53-171">Defining Object Types and Formatting</span></span>

<span data-ttu-id="7db53-172">Windows PowerShell 使用 .Net 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="7db53-172">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="7db53-173">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="7db53-173">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="7db53-174">如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="7db53-174">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="7db53-175">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7db53-175">Building the Cmdlet</span></span>

<span data-ttu-id="7db53-176">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。</span><span class="sxs-lookup"><span data-stu-id="7db53-176">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="7db53-177">如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="7db53-177">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="7db53-178">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7db53-178">Testing the Cmdlet</span></span>

<span data-ttu-id="7db53-179">當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="7db53-179">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="7db53-180">以下是數個測試 Stop-Proc Cmdlet 的測試。</span><span class="sxs-lookup"><span data-stu-id="7db53-180">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="7db53-181">如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="7db53-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="7db53-182">開始 Windows PowerShell，並使用 Stop-Proc Cmdlet 來停止處理，如下所示。</span><span class="sxs-lookup"><span data-stu-id="7db53-182">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="7db53-183">因為 Cmdlet 會將 `Name` 參數指定為強制參數，所以 Cmdlet 會查詢參數。</span><span class="sxs-lookup"><span data-stu-id="7db53-183">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="7db53-184">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7db53-184">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="7db53-185">現在讓我們使用 Cmdlet 來停止名為 "NOTEPAD" 的進程。</span><span class="sxs-lookup"><span data-stu-id="7db53-185">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="7db53-186">此 Cmdlet 會要求您確認動作。</span><span class="sxs-lookup"><span data-stu-id="7db53-186">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

    <span data-ttu-id="7db53-187">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7db53-187">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="7db53-188">使用如下所示的 Stop-Proc 來停止名為 "WINLOGON" 的重要進程。</span><span class="sxs-lookup"><span data-stu-id="7db53-188">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="7db53-189">系統會提示您執行此動作，並對其發出警告，因為這會導致作業系統重新開機。</span><span class="sxs-lookup"><span data-stu-id="7db53-189">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    <span data-ttu-id="7db53-190">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7db53-190">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="7db53-191">現在讓我們嘗試停止 WINLOGON 進程，而不會收到警告。</span><span class="sxs-lookup"><span data-stu-id="7db53-191">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="7db53-192">請注意，此命令專案會使用 `Force` 參數來覆寫警告。</span><span class="sxs-lookup"><span data-stu-id="7db53-192">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    <span data-ttu-id="7db53-193">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7db53-193">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="7db53-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7db53-194">See Also</span></span>

[<span data-ttu-id="7db53-195">加入處理 Command-Line 輸入的參數</span><span class="sxs-lookup"><span data-stu-id="7db53-195">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="7db53-196">[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7db53-196">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="7db53-197">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="7db53-197">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="7db53-198">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7db53-198">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="7db53-199">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="7db53-199">Cmdlet Samples</span></span>](./cmdlet-samples.md)
