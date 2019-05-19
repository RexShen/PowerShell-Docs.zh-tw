---
title: 加入處理管線輸入的參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: def0ac2ff98575beb29c3c2a7d91a5a5c53e648e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854988"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="09334-102">新增處理管道輸入的參數</span><span class="sxs-lookup"><span data-stu-id="09334-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="09334-103">其中一個的 cmdlet 來源是輸入的來自上游的 cmdlet 從管線上的物件。</span><span class="sxs-lookup"><span data-stu-id="09334-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="09334-104">本節說明如何將參數新增至 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))，讓此指令程式可以處理管線的物件。</span><span class="sxs-lookup"><span data-stu-id="09334-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="09334-105">此 Get-proc cmdlet 會使用`Name`接受來自管線的物件中，輸入的參數會從本機電腦，根據提供的名稱，擷取程序資訊，並接著會處理序的相關資訊顯示在命令列。</span><span class="sxs-lookup"><span data-stu-id="09334-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="09334-106">定義在 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="09334-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="09334-107">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="09334-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="09334-108">此 cmdlet 可擷取處理序資訊，因此在這裡選擇的指令動詞名稱是 「 Get 」。</span><span class="sxs-lookup"><span data-stu-id="09334-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="09334-109">（幾乎任何一種能夠擷取資訊的指令程式可以處理命令列輸入）。如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="09334-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="09334-110">以下是此 Get-proc cmdlet 的定義。</span><span class="sxs-lookup"><span data-stu-id="09334-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="09334-111">會提供此定義的詳細資料[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="09334-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="09334-112">定義從管線輸入</span><span class="sxs-lookup"><span data-stu-id="09334-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="09334-113">本章節描述如何定義從 cmdlet 管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="09334-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="09334-114">此 Get-proc cmdlet 定義屬性，表示`Name`參數中所述[加入參數，該程序的命令列輸入](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="09334-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="09334-115">（請參閱該主題，以宣告參數的一般資訊）。</span><span class="sxs-lookup"><span data-stu-id="09334-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="09334-116">不過，當 cmdlet 需要處理管線的輸入，它必須具有其繫結至輸入值，Windows PowerShell 執行階段的參數。</span><span class="sxs-lookup"><span data-stu-id="09334-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="09334-117">若要這樣做，您必須新增`ValueFromPipeline`關鍵字或加入`ValueFromPipelineByProperty`關鍵字來[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="09334-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="09334-118">指定`ValueFromPipeline`關鍵字，如果此指令程式會存取完整的輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="09334-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="09334-119">指定`ValueFromPipelineByProperty`如果 cmdlet 會在存取物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="09334-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="09334-120">以下是參數宣告`Name`接受管線輸入此 Get-proc cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="09334-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<span data-ttu-id="09334-121">先前的宣告集`ValueFromPipeline`關鍵字來`true`，讓 Windows PowerShell 執行階段將參數繫結至連入物件的物件是否相同的型別，做為參數，或如果它可以強制轉型為相同的類型。</span><span class="sxs-lookup"><span data-stu-id="09334-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="09334-122">`ValueFromPipelineByPropertyName`關鍵字也會設定為`true`如此，Windows PowerShell 執行階段會檢查傳入物件`Name`屬性。</span><span class="sxs-lookup"><span data-stu-id="09334-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="09334-123">如果連入的物件會有這類屬性，執行階段會繫結`Name`參數來`Name`連入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="09334-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="09334-124">設定`ValueFromPipeline`屬性 (attribute) 關鍵字參數的優先順序高於設定`ValueFromPipelineByPropertyName`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="09334-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="09334-125">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="09334-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="09334-126">如果您的 cmdlet 是處理管線輸入，它必須覆寫適當的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="09334-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="09334-127">在中引進的基本輸入的處理方法[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="09334-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="09334-128">此 Get-proc cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來處理`Name`使用者或指令碼所提供的參數輸入。</span><span class="sxs-lookup"><span data-stu-id="09334-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="09334-129">如果未提供名稱，這個方法會取得每個要求的處理序名稱或所有處理程序的程序。</span><span class="sxs-lookup"><span data-stu-id="09334-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="09334-130">請注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，來呼叫[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)是輸出機制，將輸出傳送到管線的物件。</span><span class="sxs-lookup"><span data-stu-id="09334-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="09334-131">此呼叫中，第二個參數`enumerateCollection`，設定為`true`告訴 Windows PowerShell 執行階段列舉的處理程序物件的陣列和一個處理序一次寫入命令列。</span><span class="sxs-lookup"><span data-stu-id="09334-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="09334-132">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="09334-132">Code Sample</span></span>

<span data-ttu-id="09334-133">完整C#程式碼範例，請參閱 < [GetProcessSample03 範例](./getprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="09334-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="09334-134">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="09334-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="09334-135">Windows PowerShell cmdlet 使用.Net 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="09334-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="09334-136">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09334-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="09334-137">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="09334-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="09334-138">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="09334-138">Building the Cmdlet</span></span>

<span data-ttu-id="09334-139">在實作必須向 Windows PowerShell，透過 Windows PowerShell cmdlet 之後嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="09334-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="09334-140">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="09334-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="09334-141">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09334-141">Testing the Cmdlet</span></span>

<span data-ttu-id="09334-142">當尚未註冊 Windows PowerShell cmdlet 時，請執行命令列上測試。</span><span class="sxs-lookup"><span data-stu-id="09334-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="09334-143">例如，測試此範例指令程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="09334-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="09334-144">如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="09334-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="09334-145">在 Windows PowerShell 提示字元中，輸入下列命令來擷取在管線處理程序名稱。</span><span class="sxs-lookup"><span data-stu-id="09334-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="09334-146">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="09334-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="09334-147">輸入下列行以取得處理程序物件具有`Name`從程序，稱為 「 IEXPLORE"的屬性。</span><span class="sxs-lookup"><span data-stu-id="09334-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="09334-148">這個範例會使用`Get-Process`為上游的命令，以擷取 「 IEXPLORE"處理序 （Windows PowerShell 所提供） 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09334-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="09334-149">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="09334-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="09334-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09334-150">See Also</span></span>

[<span data-ttu-id="09334-151">加入處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="09334-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="09334-152">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09334-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="09334-153">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="09334-153">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="09334-154">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="09334-154">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="09334-155">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="09334-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="09334-156">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="09334-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
