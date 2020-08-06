---
title: 加入處理管線輸入的參數 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.openlocfilehash: a678df30a13086b317d5680ee0fbc4d3c3391235
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784549"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="4db71-102">新增處理管道輸入的參數</span><span class="sxs-lookup"><span data-stu-id="4db71-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="4db71-103">Cmdlet 的其中一個輸入來源是管線上源自上游 Cmdlet 的物件。</span><span class="sxs-lookup"><span data-stu-id="4db71-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="4db71-104">本節說明如何將參數新增至 ([建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)) 中所述的 Get-Proc Cmdlet，讓 Cmdlet 可以處理管線物件。</span><span class="sxs-lookup"><span data-stu-id="4db71-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="4db71-105">這個程式碼 Cmdlet `Name` 會使用接受管線物件輸入的參數，根據提供的名稱從本機電腦抓取處理資訊，然後在命令列中顯示進程的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4db71-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="4db71-106">定義 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="4db71-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="4db71-107">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="4db71-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="4db71-108">此 Cmdlet 會抓取處理常式資訊，因此此處選擇的動詞名稱是 "Get"。</span><span class="sxs-lookup"><span data-stu-id="4db71-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="4db71-109"> (幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入。 ) 如需已核准 Cmdlet 動詞的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="4db71-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="4db71-110">以下是這個 Get-Proc Cmdlet 的定義。</span><span class="sxs-lookup"><span data-stu-id="4db71-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="4db71-111">[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)會提供此定義的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4db71-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="4db71-112">從管線定義輸入</span><span class="sxs-lookup"><span data-stu-id="4db71-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="4db71-113">本節說明如何從管線定義 Cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="4db71-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="4db71-114">此 Proc Cmdlet 會定義代表參數的屬性， `Name` 如[新增處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="4db71-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>
<span data-ttu-id="4db71-115"> (參閱該主題，以取得宣告參數的一般資訊。 ) </span><span class="sxs-lookup"><span data-stu-id="4db71-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="4db71-116">不過，當 Cmdlet 需要處理管線輸入時，Windows PowerShell 執行時間必須將其參數系結至輸入值。</span><span class="sxs-lookup"><span data-stu-id="4db71-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="4db71-117">若要這樣做，您必須新增 `ValueFromPipeline` 關鍵字，或將 `ValueFromPipelineByProperty` 關鍵字加入[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告中。</span><span class="sxs-lookup"><span data-stu-id="4db71-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="4db71-118">`ValueFromPipeline`如果 Cmdlet 存取完整的輸入物件，請指定關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4db71-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="4db71-119">`ValueFromPipelineByProperty`如果 Cmdlet 只存取物件的屬性，請指定。</span><span class="sxs-lookup"><span data-stu-id="4db71-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="4db71-120">以下是 `Name` 接受管線輸入之這個 Get-Proc Cmdlet 之參數的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="4db71-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="35-44":::

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

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="4db71-121">先前的宣告會將關鍵字設為，如此一來， `ValueFromPipeline` `true` 如果物件的類型與參數相同，或者可以強制轉型為相同的類型，Windows PowerShell 執行時間就會將參數系結至傳入物件。</span><span class="sxs-lookup"><span data-stu-id="4db71-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="4db71-122">`ValueFromPipelineByPropertyName`關鍵字也設定為， `true` 因此 Windows PowerShell 執行時間會檢查屬性的傳入物件 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="4db71-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="4db71-123">如果傳入的物件具有這類屬性，則執行時間會將 `Name` 參數系結至 `Name` 傳入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="4db71-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="4db71-124">`ValueFromPipeline`參數的屬性關鍵字設定會優先于關鍵字的設定 `ValueFromPipelineByPropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="4db71-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="4db71-125">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="4db71-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="4db71-126">如果您的 Cmdlet 是用來處理管線輸入，它必須覆寫適當的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="4db71-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="4db71-127">基本輸入處理方法會在[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)中引進。</span><span class="sxs-lookup"><span data-stu-id="4db71-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="4db71-128">此 Proc Cmdlet 會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理 `Name` 使用者或腳本所提供的參數輸入。</span><span class="sxs-lookup"><span data-stu-id="4db71-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="4db71-129">如果未提供任何名稱，這個方法會取得每個要求的進程名稱或所有進程的進程。</span><span class="sxs-lookup"><span data-stu-id="4db71-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="4db71-130">請注意，在[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中，對 WriteObject 的呼叫[ (system.object，system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)是將輸出物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="4db71-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="4db71-131">這個呼叫的第二個參數 `enumerateCollection` 會設定為， `true` 以指示 Windows PowerShell 執行時間列舉處理常式物件的陣列，並一次將一個進程寫入命令列。</span><span class="sxs-lookup"><span data-stu-id="4db71-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="4db71-132">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4db71-132">Code Sample</span></span>

<span data-ttu-id="4db71-133">如需完整的 c # 範例程式碼，請參閱[GetProcessSample03 範例](./getprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="4db71-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="4db71-134">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="4db71-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="4db71-135">Windows PowerShell 會使用 .Net 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="4db71-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="4db71-136">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="4db71-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="4db71-137">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="4db71-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="4db71-138">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4db71-138">Building the Cmdlet</span></span>

<span data-ttu-id="4db71-139">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="4db71-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4db71-140">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="4db71-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4db71-141">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4db71-141">Testing the Cmdlet</span></span>

<span data-ttu-id="4db71-142">當您的 Cmdlet 已向 Windows PowerShell 註冊時，請在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="4db71-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="4db71-143">例如，測試範例 Cmdlet 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4db71-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="4db71-144">如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="4db71-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="4db71-145">在 Windows PowerShell 提示字元中，輸入下列命令以透過管線抓取進程名稱。</span><span class="sxs-lookup"><span data-stu-id="4db71-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

  ```powershell
  PS> type ProcessNames | get-proc
  ```

  <span data-ttu-id="4db71-146">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4db71-146">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      809      21  40856    4448    147    9.50  2288  iexplore
      737      21  26036   16348    144   22.03  3860  iexplore
       39       2   1024     388     30    0.08  3396  notepad
     3927      62  71836   26984    467  195.19  1848  OUTLOOK
  ```

- <span data-ttu-id="4db71-147">輸入下列幾行，以 `Name` 從名為 "iexplore.exe" 的進程取得具有屬性的處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="4db71-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="4db71-148">這個範例會使用 `Get-Process` Windows PowerShell 所提供的 Cmdlet () 作為上游命令來抓取 "iexplore.exe" 進程。</span><span class="sxs-lookup"><span data-stu-id="4db71-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  <span data-ttu-id="4db71-149">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4db71-149">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a><span data-ttu-id="4db71-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4db71-150">See Also</span></span>

[<span data-ttu-id="4db71-151">新增處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="4db71-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="4db71-152">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4db71-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="4db71-153">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4db71-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="4db71-154">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4db71-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="4db71-155">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="4db71-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="4db71-156">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="4db71-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
