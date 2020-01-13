---
title: 建立可修改系統的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365757"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="494db-102">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="494db-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="494db-103">有時候，Cmdlet 必須修改系統的執行狀態，而不只是 Windows PowerShell 執行時間的狀態。</span><span class="sxs-lookup"><span data-stu-id="494db-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="494db-104">在這些情況下，Cmdlet 應該會讓使用者有機會確認是否要進行變更。</span><span class="sxs-lookup"><span data-stu-id="494db-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="494db-105">若要支援確認，Cmdlet 必須執行兩項動作。</span><span class="sxs-lookup"><span data-stu-id="494db-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="494db-106">宣告 Cmdlet 會在您指定[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性時，藉由將 SupportsShouldProcess 關鍵字設定為 `true`，來支援確認。</span><span class="sxs-lookup"><span data-stu-id="494db-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="494db-107">執行 Cmdlet 時，請呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （如下列範例所示）：。</span><span class="sxs-lookup"><span data-stu-id="494db-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="494db-108">藉由支援確認，Cmdlet 會公開 Windows PowerShell 所提供的 `Confirm` 和 `WhatIf` 參數，也符合 Cmdlet 的開發指導方針（如需 Cmdlet 開發指導方針的詳細資訊，請參閱[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)）。</span><span class="sxs-lookup"><span data-stu-id="494db-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="494db-109">變更系統</span><span class="sxs-lookup"><span data-stu-id="494db-109">Changing the System</span></span>

<span data-ttu-id="494db-110">「變更系統」的動作是指任何可能變更 Windows PowerShell 外部系統狀態的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="494db-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="494db-111">例如，停止處理常式、啟用或停用使用者帳戶，或將資料列加入至資料庫資料表，全都會變更應該確認的系統。</span><span class="sxs-lookup"><span data-stu-id="494db-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="494db-112">相反地，讀取資料或建立暫時性連線的作業並不會變更系統，而且通常不需要確認。</span><span class="sxs-lookup"><span data-stu-id="494db-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="494db-113">對於其效果限制在 Windows PowerShell 執行時間內部的動作（例如 `set-variable`），也不需要確認。</span><span class="sxs-lookup"><span data-stu-id="494db-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="494db-114">可能或可能不會進行持續性變更的 Cmdlet 應該宣告 `SupportsShouldProcess`，並[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只在即將進行持續變更時才呼叫。</span><span class="sxs-lookup"><span data-stu-id="494db-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="494db-115">ShouldProcess 確認僅適用于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="494db-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="494db-116">如果命令或腳本藉由直接呼叫 .NET 方法或屬性來修改系統的執行狀態，或在 Windows PowerShell 外部呼叫應用程式，則無法使用這種形式的確認。</span><span class="sxs-lookup"><span data-stu-id="494db-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="494db-117">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="494db-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="494db-118">本主題描述的停止程式 Cmdlet 會嘗試停止使用 Get-Proc Cmdlet 抓取的進程（如[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)所述）。</span><span class="sxs-lookup"><span data-stu-id="494db-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="494db-119">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="494db-119">Defining the Cmdlet</span></span>

<span data-ttu-id="494db-120">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="494db-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="494db-121">因為您要撰寫 Cmdlet 來變更系統，所以應該據以命名。</span><span class="sxs-lookup"><span data-stu-id="494db-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="494db-122">此 Cmdlet 會停止系統進程，因此此處選擇的動詞名稱是 "Stop" （由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別所定義），其名詞為 "Proc"，表示 Cmdlet 會停止處理常式。</span><span class="sxs-lookup"><span data-stu-id="494db-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="494db-123">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="494db-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="494db-124">以下是這個 Stop-Proc Cmdlet 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="494db-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="494db-125">請注意，在 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)宣告中，`SupportsShouldProcess` 屬性關鍵字會設定為 `true`，以啟用 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的呼叫，以進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="494db-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="494db-126">若未設定此關鍵字，使用者將無法使用 `Confirm` 和 `WhatIf` 參數。</span><span class="sxs-lookup"><span data-stu-id="494db-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="494db-127">極具破壞性的動作</span><span class="sxs-lookup"><span data-stu-id="494db-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="494db-128">某些作業是非常破壞性的，例如重新格式化使用中的硬碟磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="494db-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="494db-129">在這些情況下，Cmdlet 應該在宣告[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性時，設定 `ConfirmImpact` = `ConfirmImpact.High`。</span><span class="sxs-lookup"><span data-stu-id="494db-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="494db-130">此設定會強制 Cmdlet 要求使用者確認，即使使用者尚未指定 `Confirm` 參數也一樣。</span><span class="sxs-lookup"><span data-stu-id="494db-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="494db-131">不過，Cmdlet 開發人員應該避免超 `ConfirmImpact` 只是可能破壞性的作業，例如刪除使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="494db-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="494db-132">請記住，如果 `ConfirmImpact` 設定為[ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**。</span><span class="sxs-lookup"><span data-stu-id="494db-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="494db-133">同樣地，某些作業不太可能會成為破壞性，雖然它們在理論上會修改 Windows PowerShell 外部系統的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="494db-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="494db-134">這類 Cmdlet 可以將 `ConfirmImpact` 設定為[Confirmimpact。](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)</span><span class="sxs-lookup"><span data-stu-id="494db-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="494db-135">這會略過使用者要求確認僅限中度影響和高影響作業的確認要求。</span><span class="sxs-lookup"><span data-stu-id="494db-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="494db-136">定義系統修改的參數</span><span class="sxs-lookup"><span data-stu-id="494db-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="494db-137">本節說明如何定義 Cmdlet 參數，包括支援系統修改所需的參數。</span><span class="sxs-lookup"><span data-stu-id="494db-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="494db-138">如果您需要定義參數的一般資訊，請參閱[新增處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="494db-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="494db-139">Stop-Proc Cmdlet 會定義三個參數： `Name`、`Force`和 `PassThru`。</span><span class="sxs-lookup"><span data-stu-id="494db-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="494db-140">`Name` 參數會對應至處理常式輸入物件的 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="494db-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="494db-141">請注意，此範例中的 `Name` 參數是必要的，因為如果 Cmdlet 沒有已命名的進程可停止，就會失敗。</span><span class="sxs-lookup"><span data-stu-id="494db-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="494db-142">`Force` 的參數可讓使用者覆寫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="494db-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="494db-143">事實上，任何呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的 Cmdlet 都應該要有 `Force` 參數，如此一來，當指定 `Force` 時，Cmdlet 就會略過[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫，並繼續操作。</span><span class="sxs-lookup"><span data-stu-id="494db-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="494db-144">請注意，這不會影響[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="494db-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="494db-145">`PassThru` 參數可讓使用者指出 Cmdlet 是否透過管線傳遞輸出物件，在此情況下，在處理常式停止後。</span><span class="sxs-lookup"><span data-stu-id="494db-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="494db-146">請注意，此參數會系結至 Cmdlet 本身，而不是系結至輸入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="494db-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="494db-147">以下是 Stop-Proc Cmdlet 的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="494db-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="494db-148">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="494db-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="494db-149">Cmdlet 必須覆寫輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="494db-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="494db-150">下列程式碼說明範例 Stop-Proc Cmdlet 中使用的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)覆寫。</span><span class="sxs-lookup"><span data-stu-id="494db-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="494db-151">這個方法會針對每個要求的進程名稱，確保進程不是特殊進程、嘗試停止進程，然後在指定 `PassThru` 參數時傳送輸出物件。</span><span class="sxs-lookup"><span data-stu-id="494db-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="494db-152">呼叫 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="494db-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="494db-153">您的 Cmdlet 的輸入處理方法應呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，以在變更（例如刪除檔案）之前確認作業執行，以進行系統的執行中狀態。</span><span class="sxs-lookup"><span data-stu-id="494db-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="494db-154">這可讓 Windows PowerShell 執行時間在 shell 中提供正確的「WhatIf」和「確認」行為。</span><span class="sxs-lookup"><span data-stu-id="494db-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="494db-155">如果 Cmdlet 所支援的指令程式應處理且無法進行[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫，使用者可能會意外地修改系統。</span><span class="sxs-lookup"><span data-stu-id="494db-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="494db-156">[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的呼叫會將要變更的資源名稱傳送給使用者，而 Windows PowerShell 執行時間會將任何命令列設定或喜好設定變數納入考慮，以決定要向使用者顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="494db-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="494db-157">下列範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ，從範例停止執行 Cmdlet 的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中進行的覆寫，以進行。</span><span class="sxs-lookup"><span data-stu-id="494db-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="494db-158">呼叫 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="494db-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="494db-159">對[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的呼叫會將次要訊息傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="494db-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="494db-160">此呼叫是在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)之後，如果 `Force` 參數未設定為 `true`，則會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="494db-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="494db-161">然後，使用者可以提供意見反應，以指出是否應該繼續操作。</span><span class="sxs-lookup"><span data-stu-id="494db-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="494db-162">您的 Cmdlet 會呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)做為額外檢查是否有潛在危險的系統修改，或當您想要為使用者提供「全部都是」和「無」所有選項時。</span><span class="sxs-lookup"><span data-stu-id="494db-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="494db-163">下列範例會示範如何呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ，從範例停止執行 Cmdlet 的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的覆寫中進行的覆寫，以進行。</span><span class="sxs-lookup"><span data-stu-id="494db-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="494db-164">停止輸入處理</span><span class="sxs-lookup"><span data-stu-id="494db-164">Stopping Input Processing</span></span>

<span data-ttu-id="494db-165">進行系統修改之 Cmdlet 的輸入處理方法必須提供一種方法來停止處理輸入。</span><span class="sxs-lookup"><span data-stu-id="494db-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="494db-166">在此停止處理指示程式的情況下，會從[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法呼叫至 System.servicemodel. Process.......[進程. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill)方法。</span><span class="sxs-lookup"><span data-stu-id="494db-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="494db-167">因為 `PassThru` 參數設定為 `true`，所以[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)也會呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) ，以將處理常式物件傳送至管線（pipeline）。</span><span class="sxs-lookup"><span data-stu-id="494db-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="494db-168">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="494db-168">Code Sample</span></span>

<span data-ttu-id="494db-169">如需完整C#的範例程式碼，請參閱[StopProcessSample01 範例](./stopprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="494db-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="494db-170">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="494db-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="494db-171">Windows PowerShell 會使用 .Net 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="494db-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="494db-172">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="494db-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="494db-173">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="494db-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="494db-174">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="494db-174">Building the Cmdlet</span></span>

<span data-ttu-id="494db-175">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="494db-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="494db-176">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="494db-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="494db-177">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="494db-177">Testing the Cmdlet</span></span>

<span data-ttu-id="494db-178">當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="494db-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="494db-179">以下是測試停止程式 Cmdlet 的數個測試。</span><span class="sxs-lookup"><span data-stu-id="494db-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="494db-180">如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="494db-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="494db-181">啟動 Windows PowerShell，並使用 Stop-Proc Cmdlet 來停止處理，如下所示。</span><span class="sxs-lookup"><span data-stu-id="494db-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="494db-182">因為 Cmdlet 會將 `Name` 參數指定為強制性，所以 Cmdlet 會查詢參數。</span><span class="sxs-lookup"><span data-stu-id="494db-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="494db-183">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="494db-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="494db-184">現在讓我們使用 Cmdlet 來停止名為 "NOTEPAD" 的進程。</span><span class="sxs-lookup"><span data-stu-id="494db-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="494db-185">Cmdlet 會要求您確認此動作。</span><span class="sxs-lookup"><span data-stu-id="494db-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="494db-186">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="494db-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="494db-187">如所示使用停止程式，以停止名為 "WINLOGON" 的關鍵進程。</span><span class="sxs-lookup"><span data-stu-id="494db-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="494db-188">系統會提示您執行此動作，並對其發出警告，因為這會導致作業系統重新開機。</span><span class="sxs-lookup"><span data-stu-id="494db-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="494db-189">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="494db-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="494db-190">現在讓我們嘗試停止 WINLOGON 進程，而不收到警告。</span><span class="sxs-lookup"><span data-stu-id="494db-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="494db-191">請注意，此命令專案會使用 `Force` 參數來覆寫警告。</span><span class="sxs-lookup"><span data-stu-id="494db-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="494db-192">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="494db-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="494db-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="494db-193">See Also</span></span>

[<span data-ttu-id="494db-194">新增可處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="494db-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="494db-195">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="494db-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="494db-196">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="494db-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="494db-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="494db-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="494db-198">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="494db-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)