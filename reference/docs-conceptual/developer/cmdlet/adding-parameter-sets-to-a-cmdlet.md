---
title: 將參數集新增至 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364587"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="5cee5-102">新增參數集到 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cee5-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="5cee5-103">有關參數集的須知事項</span><span class="sxs-lookup"><span data-stu-id="5cee5-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="5cee5-104">Windows PowerShell 會將參數集定義為一起運作的一組參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="5cee5-105">藉由將 Cmdlet 的參數分組，您可以建立單一 Cmdlet，根據使用者指定的參數群組來變更其功能。</span><span class="sxs-lookup"><span data-stu-id="5cee5-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="5cee5-106">使用兩個參數集來定義不同功能的 Cmdlet 範例，是 Windows PowerShell 所提供的 `Get-EventLog` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5cee5-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="5cee5-107">當使用者指定 `List` 或 `LogName` 參數時，此 Cmdlet 會傳回不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="5cee5-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="5cee5-108">如果指定了 `LogName` 參數，此 Cmdlet 會傳回指定事件記錄檔中事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5cee5-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="5cee5-109">如果指定了 `List` 參數，Cmdlet 會傳回記錄檔本身的相關資訊（而不是其包含的事件資訊）。</span><span class="sxs-lookup"><span data-stu-id="5cee5-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="5cee5-110">在此情況下，`List` 和 @no__t 1 參數會識別兩個不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="5cee5-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="5cee5-111">有關參數集的兩個重要事項，就是 Windows PowerShell 執行時間只會針對特定輸入使用一個參數集，而且每個參數集必須至少有一個參數是該參數集唯一的。</span><span class="sxs-lookup"><span data-stu-id="5cee5-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="5cee5-112">為了說明最後一點，此停止程式指令程式會使用三個參數集： `ProcessName`、`ProcessId` 和 `InputObject`。</span><span class="sxs-lookup"><span data-stu-id="5cee5-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="5cee5-113">每個參數集都有一個不在其他參數集內的參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="5cee5-114">參數集可以共用其他參數，但此 Cmdlet 會使用唯一參數 `ProcessName`，`ProcessId`，而 `InputObject`，以識別 Windows PowerShell 執行時間應該使用的參數集。</span><span class="sxs-lookup"><span data-stu-id="5cee5-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="5cee5-115">宣告 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="5cee5-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="5cee5-116">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="5cee5-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="5cee5-117">針對此 Cmdlet，會使用生命週期動詞 "Stop"，因為此 Cmdlet 會停止系統進程。</span><span class="sxs-lookup"><span data-stu-id="5cee5-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="5cee5-118">使用名詞名稱 "Proc"，因為 Cmdlet 會在進程上運作。</span><span class="sxs-lookup"><span data-stu-id="5cee5-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="5cee5-119">在下面的宣告中，請注意 Cmdlet 動詞和名詞名稱會反映在 Cmdlet 類別的名稱中。</span><span class="sxs-lookup"><span data-stu-id="5cee5-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="5cee5-120">如需已核准 Cmdlet 動詞命令名稱的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="5cee5-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5cee5-121">下列程式碼是這個停止進程 Cmdlet 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="5cee5-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="5cee5-122">宣告 Cmdlet 的參數</span><span class="sxs-lookup"><span data-stu-id="5cee5-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="5cee5-123">此 Cmdlet 會定義三個參數，做為 Cmdlet 的輸入（這些參數也會定義參數集），以及一個 @no__t 0 參數來管理 Cmdlet 的功能，以及可判斷 Cmdlet 是否傳送輸出物件的 @no__t 1 參數透過管線。</span><span class="sxs-lookup"><span data-stu-id="5cee5-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="5cee5-124">根據預設，此 Cmdlet 不會透過管線傳遞物件。</span><span class="sxs-lookup"><span data-stu-id="5cee5-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="5cee5-125">如需最後兩個參數的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="5cee5-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="5cee5-126">宣告 Name 參數</span><span class="sxs-lookup"><span data-stu-id="5cee5-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="5cee5-127">此輸入參數可讓使用者指定要停止的處理常式名稱。</span><span class="sxs-lookup"><span data-stu-id="5cee5-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="5cee5-128">請注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性的 `ParameterSetName` 屬性關鍵字會指定為此參數設定的 `ProcessName` 參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="5cee5-129">另請注意，別名 "ProcessName" 也會提供給此參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="5cee5-130">宣告 Id 參數</span><span class="sxs-lookup"><span data-stu-id="5cee5-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="5cee5-131">此輸入參數可讓使用者指定要停止之處理常式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5cee5-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="5cee5-132">請注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性的 `ParameterSetName` 屬性關鍵字會指定 `ProcessId` 參數集。</span><span class="sxs-lookup"><span data-stu-id="5cee5-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="5cee5-133">另請注意，別名 "ProcessId" 也會提供給此參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="5cee5-134">宣告 InputObject 參數</span><span class="sxs-lookup"><span data-stu-id="5cee5-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="5cee5-135">此輸入參數可讓使用者指定輸入物件，其中包含要停止之處理常式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5cee5-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="5cee5-136">請注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性的 `ParameterSetName` 屬性關鍵字會指定為此參數設定的 `InputObject` 參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="5cee5-137">另請注意，此參數沒有別名。</span><span class="sxs-lookup"><span data-stu-id="5cee5-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="5cee5-138">宣告多個參數集合中的參數</span><span class="sxs-lookup"><span data-stu-id="5cee5-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="5cee5-139">雖然每個參數集都必須有唯一的參數，但參數可以屬於一個以上的參數集。</span><span class="sxs-lookup"><span data-stu-id="5cee5-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="5cee5-140">在這些情況下，請為此參數所屬的每個集合，提供[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告給 shared 參數。</span><span class="sxs-lookup"><span data-stu-id="5cee5-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="5cee5-141">如果參數是在所有參數集中，您只需要宣告參數屬性一次，而不需要指定參數集名稱。</span><span class="sxs-lookup"><span data-stu-id="5cee5-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="5cee5-142">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="5cee5-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="5cee5-143">每個 Cmdlet 都必須覆寫輸入處理方法，這通常會是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="5cee5-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="5cee5-144">在此 Cmdlet 中，會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，讓 Cmdlet 可以處理任何數目的進程。</span><span class="sxs-lookup"><span data-stu-id="5cee5-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="5cee5-145">它包含一個 Select 語句，它會根據使用者指定的參數集來呼叫不同的方法。</span><span class="sxs-lookup"><span data-stu-id="5cee5-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="5cee5-146">這裡不會說明 Select 語句所呼叫的 Helper 方法，但您可以在下一節的完整程式碼範例中看到其實作為。</span><span class="sxs-lookup"><span data-stu-id="5cee5-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5cee5-147">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="5cee5-147">Code Sample</span></span>

<span data-ttu-id="5cee5-148">如需完整C#的範例程式碼，請參閱[StopProcessSample04 範例](./stopprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="5cee5-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="5cee5-149">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="5cee5-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="5cee5-150">Windows PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="5cee5-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="5cee5-151">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="5cee5-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="5cee5-152">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5cee5-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5cee5-153">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cee5-153">Building the Cmdlet</span></span>

<span data-ttu-id="5cee5-154">在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="5cee5-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="5cee5-155">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="5cee5-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5cee5-156">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cee5-156">Testing the Cmdlet</span></span>

<span data-ttu-id="5cee5-157">當您的 Cmdlet 已向 Windows PowerShell 註冊時，請在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="5cee5-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="5cee5-158">以下是一些測試，示範如何使用 `ProcessId` 和 @no__t 1 參數來測試其參數集以停止進程。</span><span class="sxs-lookup"><span data-stu-id="5cee5-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="5cee5-159">當 Windows PowerShell 啟動時，請使用設定的 `ProcessId` 參數來執行停止程式 Cmdlet，以根據其識別碼停止進程。</span><span class="sxs-lookup"><span data-stu-id="5cee5-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="5cee5-160">在此情況下，Cmdlet 會使用 `ProcessId` 參數集來停止進程。</span><span class="sxs-lookup"><span data-stu-id="5cee5-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="5cee5-161">當 Windows PowerShell 啟動時，請執行停止操作 Cmdlet，並將 `InputObject` 參數設定為在 `Get-Process` 命令所抓取的記事本物件上停止處理常式。</span><span class="sxs-lookup"><span data-stu-id="5cee5-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="5cee5-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cee5-162">See Also</span></span>

[<span data-ttu-id="5cee5-163">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cee5-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="5cee5-164">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cee5-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="5cee5-165">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5cee5-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="5cee5-166">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5cee5-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="5cee5-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5cee5-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
