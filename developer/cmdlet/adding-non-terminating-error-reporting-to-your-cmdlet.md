---
title: 新增非終止錯誤報告到您的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: e0550dacc33f45f45ba105ca5cb4d2e5b5d675fb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056051"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="6f5ce-102">新增非終止錯誤報告到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f5ce-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="6f5ce-103">指令程式可以藉由呼叫報告非終止錯誤[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法還是繼續執行進一步的連入或目前的輸入物件上的作業和管線的物件。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="6f5ce-104">本節說明如何建立 cmdlet 會報告非終止錯誤，從其輸入的處理方法。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="6f5ce-105">非終止錯誤 （以及終止錯誤），此指令程式必須通過[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)識別錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identifying the error.</span></span> <span data-ttu-id="6f5ce-106">識別每個錯誤記錄的唯一字串，稱為 「 錯誤識別碼 」。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-106">Each error record is identified by a unique string called the "error identifier."</span></span> <span data-ttu-id="6f5ce-107">除了識別項，每個錯誤類別目錄由所定義的常數[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="6f5ce-108">使用者可以檢視根據其類別，藉由設定錯誤`$ErrorView`變數設為"CategoryView 」。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="6f5ce-109">如需詳細的錯誤記錄的詳細資訊，請參閱[Windows PowerShell 的錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="6f5ce-110">在本節中的主題包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="6f5ce-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="6f5ce-111">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="6f5ce-111">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="6f5ce-112">定義參數</span><span class="sxs-lookup"><span data-stu-id="6f5ce-112">Defining Parameters</span></span>](#Defining-Parameters)

- [<span data-ttu-id="6f5ce-113">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="6f5ce-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="6f5ce-114">報告非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="6f5ce-114">Reporting Nonterminating Errors</span></span>](#Reporting-Nonterminating-Errors)

- [<span data-ttu-id="6f5ce-115">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6f5ce-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="6f5ce-116">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="6f5ce-116">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="6f5ce-117">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="6f5ce-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="6f5ce-118">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f5ce-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="6f5ce-119">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="6f5ce-119">Defining the Cmdlet</span></span>

<span data-ttu-id="6f5ce-120">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="6f5ce-121">此 cmdlet 可擷取處理序資訊，因此在這裡選擇的指令動詞名稱是 「 Get 」。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-121">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="6f5ce-122">（幾乎任何一種能夠擷取資訊的指令程式可以處理命令列輸入）。如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-122">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="6f5ce-123">以下是此 Get-proc cmdlet 的定義。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-123">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="6f5ce-124">會提供此定義的詳細資料[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-124">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="6f5ce-125">定義參數</span><span class="sxs-lookup"><span data-stu-id="6f5ce-125">Defining Parameters</span></span>

<span data-ttu-id="6f5ce-126">如有必要，您的 cmdlet 必須定義來處理輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-126">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="6f5ce-127">定義此 Get-proc cmdlet`Name`參數中所述[加入參數，該程序的命令列輸入](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-127">This Get-Proc cmdlet defines a `Name` parameter as described in [Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="6f5ce-128">以下是參數宣告`Name`此 Get-proc cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="6f5ce-129">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="6f5ce-129">Overriding Input Processing Methods</span></span>

<span data-ttu-id="6f5ce-130">所有 cmdlet 必須覆都寫的輸入處理所提供的方法之一[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-130">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="6f5ce-131">這些方法中會討論[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-131">These methods are discussed in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6f5ce-132">您的 cmdlet 應該盡可能獨立處理每一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-132">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="6f5ce-133">此 Get-proc cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來處理`Name`參數提供的使用者或指令碼輸入。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-133">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter for input provided by the user or a script.</span></span> <span data-ttu-id="6f5ce-134">如果未提供名稱，這個方法會取得每個要求的處理序名稱或所有處理程序的程序。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-134">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="6f5ce-135">此覆寫的詳細資料指定於[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-135">Details of this override are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

#### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="6f5ce-136">報告錯誤時的注意事項</span><span class="sxs-lookup"><span data-stu-id="6f5ce-136">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="6f5ce-137">[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)物件寫入錯誤需要在本質上發生例外狀況時，將傳遞此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-137">The [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="6f5ce-138">決定要使用的例外狀況時，請遵循的.NET 指導方針。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-138">Follow the .NET guidelines when determining the exception to use.</span></span> <span data-ttu-id="6f5ce-139">基本上，如果發生錯誤語意上與現有的例外狀況相同，則指令程式應該使用，或衍生自該例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-139">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="6f5ce-140">否則，它應該衍生新的例外狀況或例外狀況階層架構，直接從[System.Exception](/dotnet/api/System.Exception)類別。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-140">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception](/dotnet/api/System.Exception) class.</span></span>

<span data-ttu-id="6f5ce-141">建立錯誤 （透過 ErrorRecord 類別 FullyQualifiedErrorId 屬性存取） 的識別項時請下列記住。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-141">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="6f5ce-142">使用目標和診斷之用，以便檢查完整的識別碼時，您就可以判斷哪些錯誤是錯誤的來源位置的字串。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-142">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="6f5ce-143">格式正確且完整的錯誤識別碼可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-143">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

<span data-ttu-id="6f5ce-144">請注意，在上述範例中，錯誤識別碼 （第一個語彙基元） 將指定的錯誤訊息的是，其餘部分會指出錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-144">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="6f5ce-145">更複雜的情況下，錯誤識別碼可以是可剖析在檢查點分隔權杖。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-145">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="6f5ce-146">這可讓您太分支上的部分錯誤識別項以及錯誤的識別碼和錯誤分類。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-146">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="6f5ce-147">此指令程式應該將特定的錯誤識別碼指派給不同的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-147">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="6f5ce-148">記住下列資訊進行指派的錯誤識別碼：</span><span class="sxs-lookup"><span data-stu-id="6f5ce-148">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="6f5ce-149">錯誤識別碼應該維持在 cmdlet 生命週期。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-149">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="6f5ce-150">不會變更錯誤識別項 cmdlet 版本之間的語意。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-150">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="6f5ce-151">使用文字 tersely 對應到所回報的錯誤之錯誤識別項。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-151">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="6f5ce-152">請勿使用空格或標點符號。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-152">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="6f5ce-153">有 cmdlet 產生的可重現錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-153">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="6f5ce-154">比方說，它不應該產生識別碼，其中包含處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-154">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="6f5ce-155">這些對應會遇到相同問題的其他使用者所看到的識別項時，才，錯誤識別碼很實用的使用者。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-155">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="6f5ce-156">未處理例外狀況未攔截的 Windows PowerShell 中的下列條件：</span><span class="sxs-lookup"><span data-stu-id="6f5ce-156">Unhandled exceptions are not caught by Windows PowerShell in the following conditions:</span></span>

- <span data-ttu-id="6f5ce-157">Cmdlet 會建立新的執行緒，並執行，因為執行緒擲回未處理的例外狀況的程式碼，如果 Windows PowerShell 不會攔截錯誤，並將會終止處理序。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-157">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="6f5ce-158">如果物件有其解構函式或 Dispose 方法中造成未處理的例外狀況的程式碼，Windows PowerShell 不會攔截錯誤，並將會終止處理序。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-158">If an object has code in its destructor or Dispose methods that causes an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="6f5ce-159">報告非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="6f5ce-159">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="6f5ce-160">輸入處理方法的任何一個可以回報給輸出資料流使用的非終止錯誤[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-160">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="6f5ce-161">以下是程式碼範例說明如何呼叫這個 Get-proc cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)從內的覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-161">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="6f5ce-162">在此情況下，如果此 cmdlet 找不到處理程序指定的處理序識別碼可以進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-162">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="6f5ce-163">要寫入非終止錯誤，必須注意的事項</span><span class="sxs-lookup"><span data-stu-id="6f5ce-163">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="6f5ce-164">對於非終止錯誤，此指令程式必須產生每個特定的輸入物件的特定錯誤識別碼。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-164">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="6f5ce-165">若要修改所產生的非終止錯誤的 Windows PowerShell 動作經常需要 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-165">A cmdlet frequently needs to modify the Windows PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="6f5ce-166">其做法是定義`ErrorAction`和`ErrorVariable`參數。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-166">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="6f5ce-167">如果定義`ErrorAction`參數，cmdlet 會顯示 user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference)，您可以設定，以也會直接影響動作`$ErrorActionPreference`變數。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-167">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="6f5ce-168">Cmdlet 可以儲存為變數使用的非終止錯誤`ErrorVariable`參數，它的設定不會影響`ErrorAction`。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-168">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="6f5ce-169">失敗可以附加至現有的錯誤變數加上加號 （+） 的變數名稱前面。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-169">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6f5ce-170">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6f5ce-170">Code Sample</span></span>

<span data-ttu-id="6f5ce-171">完整C#程式碼範例，請參閱 < [GetProcessSample04 範例](./getprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-171">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="6f5ce-172">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="6f5ce-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="6f5ce-173">Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-173">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="6f5ce-174">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-174">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="6f5ce-175">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="6f5ce-176">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="6f5ce-176">Building the Cmdlet</span></span>

<span data-ttu-id="6f5ce-177">在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-177">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="6f5ce-178">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="6f5ce-179">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f5ce-179">Testing the Cmdlet</span></span>

<span data-ttu-id="6f5ce-180">當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="6f5ce-181">讓我們測試範例 Get-proc cmdlet，以查看它是否會報告錯誤：</span><span class="sxs-lookup"><span data-stu-id="6f5ce-181">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="6f5ce-182">啟動 Windows PowerShell，並使用 Get-proc cmdlet 來擷取名為"TEST"的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-182">Start Windows PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="6f5ce-183">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6f5ce-183">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="6f5ce-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f5ce-184">See Also</span></span>

[<span data-ttu-id="6f5ce-185">新增處理程序管線輸入的參數</span><span class="sxs-lookup"><span data-stu-id="6f5ce-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="6f5ce-186">加入處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="6f5ce-186">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="6f5ce-187">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f5ce-187">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="6f5ce-188">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="6f5ce-188">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="6f5ce-189">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="6f5ce-189">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="6f5ce-190">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="6f5ce-190">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6f5ce-191">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="6f5ce-191">Cmdlet Samples</span></span>](./cmdlet-samples.md)
