---
title: 將非終止錯誤報表新增至您的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364607"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="5b81c-102">新增非終止錯誤報告到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b81c-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="5b81c-103">Cmdlet 可以藉由呼叫[WriteError 的管理元件][]方法來報告非終止錯誤，並繼續在目前的輸入物件或進一步的傳入管線物件上操作。</span><span class="sxs-lookup"><span data-stu-id="5b81c-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="5b81c-104">本節說明如何建立 Cmdlet，以從其輸入處理方法報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b81c-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="5b81c-105">對於非終止錯誤（以及終止錯誤），Cmdlet 必須傳遞識別錯誤的[ErrorRecord。][]物件。</span><span class="sxs-lookup"><span data-stu-id="5b81c-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="5b81c-106">每個錯誤記錄都是由稱為「錯誤識別碼」的唯一字串所識別。</span><span class="sxs-lookup"><span data-stu-id="5b81c-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="5b81c-107">除了識別碼以外，每個錯誤的類別都是由[ErrorCategory。][]列舉所定義的常數所指定。</span><span class="sxs-lookup"><span data-stu-id="5b81c-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="5b81c-108">使用者可以將 `$ErrorView` 變數設定為 "CategoryView"，以根據其類別來查看錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b81c-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="5b81c-109">如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="5b81c-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="5b81c-110">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b81c-110">Defining the Cmdlet</span></span>

<span data-ttu-id="5b81c-111">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="5b81c-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="5b81c-112">此 Cmdlet 會抓取處理常式資訊，因此此處選擇的動詞名稱是 "Get"。</span><span class="sxs-lookup"><span data-stu-id="5b81c-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="5b81c-113">（幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入）。如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="5b81c-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5b81c-114">以下是這個 Get-Proc Cmdlet 的定義。</span><span class="sxs-lookup"><span data-stu-id="5b81c-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="5b81c-115">[建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)會提供此定義的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5b81c-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="5b81c-116">定義參數</span><span class="sxs-lookup"><span data-stu-id="5b81c-116">Defining Parameters</span></span>

<span data-ttu-id="5b81c-117">如有需要，您的 Cmdlet 必須定義用來處理輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="5b81c-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="5b81c-118">此 Get Proc Cmdlet 會定義**名稱**參數，如[新增處理命令列輸入的參數](adding-parameters-that-process-command-line-input.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="5b81c-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="5b81c-119">以下是這個 Get-Proc Cmdlet 的**Name**參數的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="5b81c-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="5b81c-120">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="5b81c-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="5b81c-121">所有 Cmdlet 都必須至少覆寫由[[系統管理]。 Cmdlet][]類別所提供的其中一個輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="5b81c-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="5b81c-122">[建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)中會討論這些方法。</span><span class="sxs-lookup"><span data-stu-id="5b81c-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5b81c-123">您的 Cmdlet 應該盡可能獨立處理每一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="5b81c-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="5b81c-124">此 Proc 指令程式會覆寫[ProcessRecord 的管理元件][]方法，以處理使用者或腳本所提供之輸入的**名稱**參數。</span><span class="sxs-lookup"><span data-stu-id="5b81c-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="5b81c-125">如果未提供任何名稱，這個方法會取得每個要求的進程名稱或所有進程的進程。</span><span class="sxs-lookup"><span data-stu-id="5b81c-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="5b81c-126">[建立您的第一個 Cmdlet](creating-a-cmdlet-without-parameters.md)會提供此覆寫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5b81c-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="5b81c-127">報告錯誤時要記住的事項</span><span class="sxs-lookup"><span data-stu-id="5b81c-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="5b81c-128">Cmdlet 在寫入錯誤時所傳遞的[ErrorRecord。][]物件，在其核心上需要例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5b81c-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="5b81c-129">判斷要使用的例外狀況時，請遵循 .NET 指導方針。</span><span class="sxs-lookup"><span data-stu-id="5b81c-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="5b81c-130">基本上，如果錯誤在語義上與現有的例外狀況相同，則 Cmdlet 應使用或衍生自該例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5b81c-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="5b81c-131">否則，它應該直接從 system.exception 類別衍生新的例外狀況或[Exception][]階層。</span><span class="sxs-lookup"><span data-stu-id="5b81c-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="5b81c-132">建立錯誤識別碼（透過 ErrorRecord 類別的 FullyQualifiedErrorId 屬性存取）時，請記住下列事項。</span><span class="sxs-lookup"><span data-stu-id="5b81c-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="5b81c-133">使用以診斷為目標的字串，以便在檢查完整識別碼時，您可以判斷錯誤是什麼，以及錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="5b81c-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="5b81c-134">正確格式的完整錯誤識別碼可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="5b81c-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="5b81c-135">請注意，在上一個範例中，錯誤識別碼（第一個 token）會指定錯誤的內容，而其餘部分則會指出錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="5b81c-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="5b81c-136">針對更複雜的案例，錯誤識別碼可以是以點分隔的標記，可以在檢查時進行剖析。</span><span class="sxs-lookup"><span data-stu-id="5b81c-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="5b81c-137">這可讓您在錯誤識別碼的部分，以及錯誤識別碼和錯誤分類中，進行分支。</span><span class="sxs-lookup"><span data-stu-id="5b81c-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="5b81c-138">Cmdlet 應該將特定的錯誤識別碼指派給不同的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="5b81c-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="5b81c-139">請記住下列資訊來指派錯誤識別碼：</span><span class="sxs-lookup"><span data-stu-id="5b81c-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="5b81c-140">在整個 Cmdlet 生命週期中，錯誤識別碼應該保持不變。</span><span class="sxs-lookup"><span data-stu-id="5b81c-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="5b81c-141">請勿變更 Cmdlet 版本之間錯誤識別碼的語法。</span><span class="sxs-lookup"><span data-stu-id="5b81c-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="5b81c-142">針對 tersely 對應至所回報錯誤的錯誤識別碼，請使用文字。</span><span class="sxs-lookup"><span data-stu-id="5b81c-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="5b81c-143">請勿使用空白字元或標點符號。</span><span class="sxs-lookup"><span data-stu-id="5b81c-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="5b81c-144">讓您的 Cmdlet 只產生可重現的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b81c-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="5b81c-145">例如，它不應該產生包含進程識別碼的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b81c-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="5b81c-146">只有當使用者對應到其他遇到相同問題的使用者所看到的識別碼時，錯誤識別碼才會很有用。</span><span class="sxs-lookup"><span data-stu-id="5b81c-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="5b81c-147">在下列情況下，PowerShell 不會攔截到未處理的例外狀況：</span><span class="sxs-lookup"><span data-stu-id="5b81c-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="5b81c-148">如果 Cmdlet 建立新的執行緒，且該執行緒中執行的程式碼擲回未處理的例外狀況，則 PowerShell 將不會攔截錯誤，並會終止進程。</span><span class="sxs-lookup"><span data-stu-id="5b81c-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="5b81c-149">如果物件在其析構函式或處置方法中有程式碼造成未處理的例外狀況，則 PowerShell 不會攔截錯誤，並會終止進程。</span><span class="sxs-lookup"><span data-stu-id="5b81c-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="5b81c-150">報告非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="5b81c-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="5b81c-151">任何一個輸入處理方法都可以使用[WriteError 的管理元件][]方法，將非終止錯誤報表到輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="5b81c-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="5b81c-152">以下是來自這個 WriteError 指令程式的程式碼範例，其中說明如何從[ProcessRecord 的管理元件][]方法的覆寫中呼叫[WriteError 的管理元件][]，以從該 Cmdlet 中取得。</span><span class="sxs-lookup"><span data-stu-id="5b81c-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="5b81c-153">在此情況下，如果 Cmdlet 找不到指定之處理序識別碼的進程，就會進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="5b81c-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="5b81c-154">撰寫非終止錯誤時應記住的事項</span><span class="sxs-lookup"><span data-stu-id="5b81c-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="5b81c-155">針對非終止錯誤，此 Cmdlet 必須為每個特定的輸入物件產生特定的錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b81c-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="5b81c-156">Cmdlet 經常需要修改非終止錯誤所產生的 PowerShell 動作。</span><span class="sxs-lookup"><span data-stu-id="5b81c-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="5b81c-157">它可以藉由定義 `ErrorAction` 和 `ErrorVariable` 參數來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="5b81c-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="5b81c-158">如果定義 `ErrorAction` 參數，此 Cmdlet 會顯示[ActionPreference。][]的使用者選項，您也可以藉由設定 `$ErrorActionPreference` 變數直接影響動作。</span><span class="sxs-lookup"><span data-stu-id="5b81c-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="5b81c-159">Cmdlet 可以使用 `ErrorVariable` 參數，將非終止錯誤儲存至變數，這不會受到 `ErrorAction`設定的影響。</span><span class="sxs-lookup"><span data-stu-id="5b81c-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="5b81c-160">您可以藉由在變數名稱前面加上加號（+），將失敗附加至現有的錯誤變數。</span><span class="sxs-lookup"><span data-stu-id="5b81c-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5b81c-161">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5b81c-161">Code Sample</span></span>

<span data-ttu-id="5b81c-162">如需完整C#的範例程式碼，請參閱[GetProcessSample04 範例](./getprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5b81c-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="5b81c-163">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="5b81c-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="5b81c-164">PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="5b81c-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="5b81c-165">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="5b81c-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="5b81c-166">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="5b81c-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5b81c-167">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b81c-167">Building the Cmdlet</span></span>

<span data-ttu-id="5b81c-168">在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="5b81c-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="5b81c-169">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="5b81c-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5b81c-170">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b81c-170">Testing the Cmdlet</span></span>

<span data-ttu-id="5b81c-171">當您的 Cmdlet 已向 PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="5b81c-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="5b81c-172">讓我們測試範例 Get-Proc Cmdlet，以查看它是否報告錯誤：</span><span class="sxs-lookup"><span data-stu-id="5b81c-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="5b81c-173">啟動 PowerShell，並使用 Get-help Cmdlet 來抓取名為 "TEST" 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5b81c-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="5b81c-174">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="5b81c-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="5b81c-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b81c-175">See Also</span></span>

[<span data-ttu-id="5b81c-176">加入處理管線輸入的參數</span><span class="sxs-lookup"><span data-stu-id="5b81c-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="5b81c-177">新增可處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="5b81c-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="5b81c-178">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b81c-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="5b81c-179">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="5b81c-179">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="5b81c-180">如何註冊 Cmdlet、提供者和主機應用程式</span><span class="sxs-lookup"><span data-stu-id="5b81c-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="5b81c-181">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="5b81c-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="5b81c-182">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="5b81c-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[Exception]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[ActionPreference。]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[ProcessRecord 的管理元件]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[WriteError 的管理元件]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
<span data-ttu-id="5b81c-187">[[系統管理]。 Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b81c-187">[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet</span></span>
[ErrorCategory。]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[ErrorRecord。]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
