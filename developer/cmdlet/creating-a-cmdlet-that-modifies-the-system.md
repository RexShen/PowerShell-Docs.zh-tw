---
title: 建立 Cmdlet 會修改系統 |Microsoft Docs
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
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068422"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="80666-102">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80666-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="80666-103">有時候指令程式必須修改系統，而不只是 Windows PowerShell 執行階段狀態的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="80666-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="80666-104">在這些情況下，此 cmdlet 應該允許使用者有機會確認要進行變更。</span><span class="sxs-lookup"><span data-stu-id="80666-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="80666-105">若要支援確認 cmdlet 必須做兩件事。</span><span class="sxs-lookup"><span data-stu-id="80666-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="80666-106">此 cmdlet 會支援確認，當您指定的宣告[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性設為 SupportsShouldProcess 關鍵字`true`。</span><span class="sxs-lookup"><span data-stu-id="80666-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="80666-107">呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （如下列範例所示），此指令程式執行期間。</span><span class="sxs-lookup"><span data-stu-id="80666-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="80666-108">藉由支援確認，cmdlet 會公開`Confirm`和`WhatIf`所提供的 Windows PowerShell，又能滿足的開發指導方針 cmdlet 的參數 （如需有關 cmdlet 開發指導方針的詳細資訊，請參閱[Cmdlet 開發指導方針](./cmdlet-development-guidelines.md)。)。</span><span class="sxs-lookup"><span data-stu-id="80666-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="80666-109">變更系統</span><span class="sxs-lookup"><span data-stu-id="80666-109">Changing the System</span></span>

<span data-ttu-id="80666-110">「 變更系統 」 動作是指任何可能會變更系統狀態的外部 Windows PowerShell 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80666-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="80666-111">例如，停止處理序，啟用或停用使用者帳戶，或加入至資料庫資料表的資料列都應該確認系統的所有變更。</span><span class="sxs-lookup"><span data-stu-id="80666-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="80666-112">相反地，作業讀取資料，或建立暫時性的連線不會變更系統，和通常不需要確認。</span><span class="sxs-lookup"><span data-stu-id="80666-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="80666-113">其效果僅限於內部，Windows PowerShell 執行階段中，這類的動作也不需要確認`set-variable`。</span><span class="sxs-lookup"><span data-stu-id="80666-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="80666-114">指令程式，可能或可能不會進行持續性的變更應該宣告`SupportsShouldProcess`並呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只有他們即將進行持續性的變更。</span><span class="sxs-lookup"><span data-stu-id="80666-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="80666-115">ShouldProcess 確認僅適用於 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80666-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="80666-116">如果命令或指令碼修改系統的執行狀態，方法是直接呼叫.NET 方法或屬性，或呼叫應用程式在 Windows PowerShell 之外，將無法使用這種形式的確認。</span><span class="sxs-lookup"><span data-stu-id="80666-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="80666-117">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80666-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="80666-118">本主題描述嘗試停止處理程序，可使用 Get-proc cmdlet 來擷取停止程序 cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="80666-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="80666-119">在本節中的主題包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="80666-119">Topics in this section include the following:</span></span>

- [<span data-ttu-id="80666-120">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="80666-120">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="80666-121">修改系統定義的參數</span><span class="sxs-lookup"><span data-stu-id="80666-121">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="80666-122">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="80666-122">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="80666-123">呼叫 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="80666-123">Calling the ShouldProcess Method</span></span>](#Calling-the-ShouldProcess-Method)

- [<span data-ttu-id="80666-124">呼叫 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="80666-124">Calling the ShouldContinue Method</span></span>](#Calling-the-ShouldContinue-Method)

- [<span data-ttu-id="80666-125">正在停止的輸入的處理</span><span class="sxs-lookup"><span data-stu-id="80666-125">Stopping Input Processing</span></span>](#Stopping-Input-Processing)

- [<span data-ttu-id="80666-126">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="80666-126">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="80666-127">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="80666-127">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="80666-128">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="80666-128">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="80666-129">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80666-129">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="80666-130">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="80666-130">Defining the Cmdlet</span></span>

<span data-ttu-id="80666-131">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="80666-131">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="80666-132">因為您正在撰寫的 cmdlet，來變更系統，它應該命名。</span><span class="sxs-lookup"><span data-stu-id="80666-132">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="80666-133">此 cmdlet 會停止系統處理序，所以在這裡選擇的指令動詞名稱是 「 停止 」，由[System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別，和名詞"Proc"，以指出此 cmdlet 會停止處理程序。</span><span class="sxs-lookup"><span data-stu-id="80666-133">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="80666-134">如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="80666-134">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="80666-135">以下是這個處理序停止外指令程式的類別定義。</span><span class="sxs-lookup"><span data-stu-id="80666-135">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="80666-136">請注意，在[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)宣告，`SupportsShouldProcess`屬性關鍵字設定為`true`若要啟用對進行呼叫 cmdlet [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="80666-136">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="80666-137">這個關鍵字設定時，沒有`Confirm`和`WhatIf`參數不會提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="80666-137">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="80666-138">極度破壞性動作</span><span class="sxs-lookup"><span data-stu-id="80666-138">Extremely Destructive Actions</span></span>

<span data-ttu-id="80666-139">有些作業是極度破壞性，例如重新格式化的作用中的硬碟磁碟分割。</span><span class="sxs-lookup"><span data-stu-id="80666-139">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="80666-140">在這些情況下，此 cmdlet 應該設定`ConfirmImpact`  =  `ConfirmImpact.High`宣告時[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性。</span><span class="sxs-lookup"><span data-stu-id="80666-140">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="80666-141">此設定會強制此 cmdlet 來要求使用者確認使用者尚未指定，即使`Confirm`參數。</span><span class="sxs-lookup"><span data-stu-id="80666-141">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="80666-142">不過，cmdlet 開發人員應避免過度使用`ConfirmImpact`為只可能破壞性，例如刪除使用者帳戶的作業。</span><span class="sxs-lookup"><span data-stu-id="80666-142">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="80666-143">請注意，如果`ConfirmImpact`設定為[System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High)。</span><span class="sxs-lookup"><span data-stu-id="80666-143">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="80666-144">同樣地，某些作業不太可能會破壞性的雖然他們不要理論上修改 Windows PowerShell 外部系統的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="80666-144">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="80666-145">此類指令程式可以設定`ConfirmImpact`要[System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)。</span><span class="sxs-lookup"><span data-stu-id="80666-145">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="80666-146">這將會略過確認要求已要求使用者確認只有中度影響和具有強烈影響的作業。</span><span class="sxs-lookup"><span data-stu-id="80666-146">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="80666-147">修改系統定義的參數</span><span class="sxs-lookup"><span data-stu-id="80666-147">Defining Parameters for System Modification</span></span>

<span data-ttu-id="80666-148">本章節描述如何定義 cmdlet 參數，包括所需的支援系統修改。</span><span class="sxs-lookup"><span data-stu-id="80666-148">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="80666-149">請參閱[加入參數，該程序的命令列輸入](./adding-parameters-that-process-command-line-input.md)如果您需要定義參數的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="80666-149">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="80666-150">停止處理序的指令程式會定義三個參數： `Name`， `Force`，和`PassThru`。</span><span class="sxs-lookup"><span data-stu-id="80666-150">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="80666-151">`Name`參數會對應至`Name`處理程序的輸入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="80666-151">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="80666-152">請注意，`Name`在此範例中的參數是必要項目，為指令程式將會失敗，如果它沒有具名的處理序停止。</span><span class="sxs-lookup"><span data-stu-id="80666-152">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="80666-153">`Force`參數可讓使用者覆寫來呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。</span><span class="sxs-lookup"><span data-stu-id="80666-153">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="80666-154">事實上，任何 cmdlet，會呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)應有`Force`參數，讓當`Force`指定，此 cmdlet 會略過呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ，並繼續處理作業。</span><span class="sxs-lookup"><span data-stu-id="80666-154">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="80666-155">請注意這不會影響呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)。</span><span class="sxs-lookup"><span data-stu-id="80666-155">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="80666-156">`PassThru`參數可讓使用者指出是否 cmdlet 會傳遞輸出物件透過管線，在此情況下，停止處理程序之後。</span><span class="sxs-lookup"><span data-stu-id="80666-156">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="80666-157">請注意，此參數繫結至 cmdlet 本身而不是屬性的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="80666-157">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="80666-158">以下是停止程序 cmdlet 的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="80666-158">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="80666-159">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="80666-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="80666-160">此指令程式，必須覆寫輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="80666-160">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="80666-161">下列程式碼說明[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)範例停止程序 cmdlet 中使用的覆寫。</span><span class="sxs-lookup"><span data-stu-id="80666-161">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="80666-162">每個要求處理程序名稱，此方法可確保程序不是特殊的處理程序，嘗試停止處理程序，並接著會傳送輸出物件，如果`PassThru`指定參數。</span><span class="sxs-lookup"><span data-stu-id="80666-162">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="80666-163">呼叫 ShouldProcess 方法</span><span class="sxs-lookup"><span data-stu-id="80666-163">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="80666-164">輸入處理方法，您的指令程式應該呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)前進行確認執行作業 （例如，刪除檔案） 變更為執行中狀態的方法在系統中。</span><span class="sxs-lookup"><span data-stu-id="80666-164">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="80666-165">這可讓 Windows PowerShell 執行階段提供正確的 「 WhatIf 」 和 「 確認 」 行為，在殼層中。</span><span class="sxs-lookup"><span data-stu-id="80666-165">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="80666-166">如果 cmdlet 可讓您指出它支援應該處理，並無法做出[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫時，使用者可能會意外地修改系統。</span><span class="sxs-lookup"><span data-stu-id="80666-166">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="80666-167">若要在呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)傳送給使用者，使用 Windows PowerShell 執行階段的任何命令列設定或喜好設定變數，請考慮變更資源的名稱在決定應該顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="80666-167">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="80666-168">下列範例示範呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)從的覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)範例中的方法停止處理序 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80666-168">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="80666-169">呼叫 ShouldContinue 方法</span><span class="sxs-lookup"><span data-stu-id="80666-169">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="80666-170">若要在呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法會將第二個訊息傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="80666-170">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="80666-171">此呼叫之後呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)會傳回`true`如果`Force`參數未設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="80666-171">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="80666-172">接著，使用者可以提供意見反應，表示作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="80666-172">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="80666-173">您 cmdlet 會呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)為有潛在危險的系統修改，或想要提供給使用者的全部是和否-all 選項時的其他檢查。</span><span class="sxs-lookup"><span data-stu-id="80666-173">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="80666-174">下列範例示範呼叫[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)從的覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)範例中的方法停止處理序 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80666-174">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="80666-175">正在停止的輸入的處理</span><span class="sxs-lookup"><span data-stu-id="80666-175">Stopping Input Processing</span></span>

<span data-ttu-id="80666-176">輸入處理方法的 cmdlet，可讓系統修改必須提供一種停止處理的輸入。</span><span class="sxs-lookup"><span data-stu-id="80666-176">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="80666-177">在此停止程序 cmdlet 的情況下進行呼叫，從[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來[System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill)方法。</span><span class="sxs-lookup"><span data-stu-id="80666-177">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="80666-178">因為`PassThru`參數設定為`true`， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)也會呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)傳送管線處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="80666-178">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="80666-179">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="80666-179">Code Sample</span></span>

<span data-ttu-id="80666-180">完整C#程式碼範例，請參閱 < [StopProcessSample01 範例](./stopprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="80666-180">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="80666-181">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="80666-181">Defining Object Types and Formatting</span></span>

<span data-ttu-id="80666-182">Windows PowerShell cmdlet 使用.Net 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="80666-182">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="80666-183">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="80666-183">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="80666-184">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="80666-184">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="80666-185">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="80666-185">Building the Cmdlet</span></span>

<span data-ttu-id="80666-186">在實作之後的 cmdlet，它必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="80666-186">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="80666-187">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="80666-187">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="80666-188">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="80666-188">Testing the Cmdlet</span></span>

<span data-ttu-id="80666-189">當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="80666-189">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="80666-190">以下是測試停止程序 cmdlet 的數個測試。</span><span class="sxs-lookup"><span data-stu-id="80666-190">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="80666-191">如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="80666-191">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="80666-192">啟動 Windows PowerShell，並使用停止程序 cmdlet 來停止處理，如下所示。</span><span class="sxs-lookup"><span data-stu-id="80666-192">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="80666-193">因為 cmdlet 會指定`Name`為必要的參數，cmdlet 查詢參數。</span><span class="sxs-lookup"><span data-stu-id="80666-193">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="80666-194">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="80666-194">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="80666-195">現在讓我們使用 cmdlet 來停止名為"NOTEPAD"的處理序。</span><span class="sxs-lookup"><span data-stu-id="80666-195">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="80666-196">此 cmdlet 會要求您確認動作。</span><span class="sxs-lookup"><span data-stu-id="80666-196">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="80666-197">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="80666-197">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="80666-198">若要停止名為"WINLOGON 」 的重要程序使用停止程序所示。</span><span class="sxs-lookup"><span data-stu-id="80666-198">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="80666-199">您會出現提示，看到有關執行此動作，因為它會造成重新啟動作業系統的警告。</span><span class="sxs-lookup"><span data-stu-id="80666-199">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="80666-200">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="80666-200">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="80666-201">讓我們現在試著停止 WINLOGON 處理程序，而不會收到一則警告。</span><span class="sxs-lookup"><span data-stu-id="80666-201">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="80666-202">請注意，此命令項目會使用`Force`參數來覆寫此警告。</span><span class="sxs-lookup"><span data-stu-id="80666-202">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="80666-203">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="80666-203">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="80666-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80666-204">See Also</span></span>

[<span data-ttu-id="80666-205">加入處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="80666-205">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="80666-206">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="80666-206">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="80666-207">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="80666-207">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="80666-208">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="80666-208">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="80666-209">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="80666-209">Cmdlet Samples</span></span>](./cmdlet-samples.md)