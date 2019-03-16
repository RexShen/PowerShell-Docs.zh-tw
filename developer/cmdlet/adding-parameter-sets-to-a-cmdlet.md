---
title: 將參數新增至 Cmdlet，設定 |Microsoft Docs
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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054980"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="36cb5-102">新增參數集到 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="36cb5-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="36cb5-103">本節說明如何新增參數集合停止處理序的指令程式 (中所述[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md))。</span><span class="sxs-lookup"><span data-stu-id="36cb5-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="36cb5-104">類似於其他程式設計人員的指南中所述的停止程序 cmdlet，此 cmdlet 會嘗試停止處理程序會擷取使用 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="36cb5-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="36cb5-105">在本節中的主題包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="36cb5-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="36cb5-106">若要了解參數集的項目</span><span class="sxs-lookup"><span data-stu-id="36cb5-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="36cb5-107">宣告 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="36cb5-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="36cb5-108">宣告 Cmdlet 的參數</span><span class="sxs-lookup"><span data-stu-id="36cb5-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="36cb5-109">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="36cb5-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="36cb5-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="36cb5-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="36cb5-111">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="36cb5-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="36cb5-112">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="36cb5-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="36cb5-113">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="36cb5-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="36cb5-114">若要了解參數集的項目</span><span class="sxs-lookup"><span data-stu-id="36cb5-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="36cb5-115">Windows PowerShell 中定義的參數集的一組一起運作的參數。</span><span class="sxs-lookup"><span data-stu-id="36cb5-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="36cb5-116">群組 cmdlet 的參數，您可以建立單一的 cmdlet，可以變更其使用者所指定的哪一個群組的參數為基礎的功能。</span><span class="sxs-lookup"><span data-stu-id="36cb5-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="36cb5-117">指令程式會使用兩個參數集來定義不同的功能，例如`Get-EventLog`所提供的 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="36cb5-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="36cb5-118">當使用者指定此 cmdlet 會傳回不同的資訊`List`或`LogName`參數。</span><span class="sxs-lookup"><span data-stu-id="36cb5-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="36cb5-119">如果`LogName`參數指定，則指令程式可傳回指定的事件記錄檔事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="36cb5-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="36cb5-120">如果`List`參數指定，則此 cmdlet 會傳回檔案本身 （不包含事件資訊） 的記錄檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="36cb5-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="36cb5-121">在此情況下，`List`和`LogName`參數會識別兩個不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="36cb5-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="36cb5-122">兩個參數集時，必須注意的重要事項是，Windows PowerShell 執行階段會使用為特定的輸入，只有一個參數，而且每個參數集，必須具有至少一個參數，都是唯一的該參數集。</span><span class="sxs-lookup"><span data-stu-id="36cb5-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="36cb5-123">為了說明這個最後一點，此處理序停止外 cmdlet 會使用三個參數集： `ProcessName`， `ProcessId`，和`InputObject`。</span><span class="sxs-lookup"><span data-stu-id="36cb5-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="36cb5-124">每一參數集合具有一個參數不是在其他的參數集。</span><span class="sxs-lookup"><span data-stu-id="36cb5-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="36cb5-125">參數集可以共用其他的參數，但此 cmdlet 會使用唯一的參數`ProcessName`， `ProcessId`，和`InputObject`來識別哪些組 Windows PowerShell 執行階段應該使用的參數。</span><span class="sxs-lookup"><span data-stu-id="36cb5-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="36cb5-126">宣告 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="36cb5-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="36cb5-127">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="36cb5-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="36cb5-128">此 cmdlet，因為此 cmdlet 會停止系統處理序，就會使用一個生命週期動詞"Stop"。</span><span class="sxs-lookup"><span data-stu-id="36cb5-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="36cb5-129">名詞 」 名稱"Proc"，因為 cmdlet 的運作方式的處理程序。</span><span class="sxs-lookup"><span data-stu-id="36cb5-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="36cb5-130">在下列宣告中，請注意 cmdlet 動詞和名詞名稱會反映在 cmdlet 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="36cb5-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="36cb5-131">如需已核准的 cmdlet 動詞名稱的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="36cb5-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="36cb5-132">下列程式碼會為此停止程序 cmdlet 類別定義。</span><span class="sxs-lookup"><span data-stu-id="36cb5-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="36cb5-133">宣告 Cmdlet 的參數</span><span class="sxs-lookup"><span data-stu-id="36cb5-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="36cb5-134">此 cmdlet 會定義做為指令程式 （這些參數也定義的參數集），輸入所需的三個參數，以及`Force`管理 cmdlet 的功能的參數和`PassThru`決定是否要傳送此 cmdlet 的參數透過管線的輸出物件。</span><span class="sxs-lookup"><span data-stu-id="36cb5-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="36cb5-135">根據預設，此 cmdlet 未通過管線的物件。</span><span class="sxs-lookup"><span data-stu-id="36cb5-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="36cb5-136">如需有關這些最後兩個參數的詳細資訊，請參閱 <<c0> [ 建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="36cb5-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="36cb5-137">宣告名稱參數</span><span class="sxs-lookup"><span data-stu-id="36cb5-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="36cb5-138">此輸入的參數可讓使用者指定要停止的處理程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="36cb5-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="36cb5-139">請注意，`ParameterSetName`屬性的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會指定`ProcessName`參數設定為此參數。</span><span class="sxs-lookup"><span data-stu-id="36cb5-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="36cb5-140">也請注意 「 ProcessName"的別名指定給這個參數。</span><span class="sxs-lookup"><span data-stu-id="36cb5-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="36cb5-141">宣告的 Id 參數</span><span class="sxs-lookup"><span data-stu-id="36cb5-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="36cb5-142">此輸入的參數可讓使用者指定要停止的處理程序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="36cb5-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="36cb5-143">請注意，`ParameterSetName`屬性的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會指定`ProcessId`參數集。</span><span class="sxs-lookup"><span data-stu-id="36cb5-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="36cb5-144">請注意，也提供給這個參數的別名"ProcessId"。</span><span class="sxs-lookup"><span data-stu-id="36cb5-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="36cb5-145">宣告 InputObject 參數</span><span class="sxs-lookup"><span data-stu-id="36cb5-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="36cb5-146">此輸入的參數可讓使用者指定輸入的物件，包含要停止處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="36cb5-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="36cb5-147">請注意，`ParameterSetName`屬性的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會指定`InputObject`參數設定為此參數。</span><span class="sxs-lookup"><span data-stu-id="36cb5-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="36cb5-148">也請注意，此參數有沒有別名。</span><span class="sxs-lookup"><span data-stu-id="36cb5-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="36cb5-149">在多個參數集中宣告參數</span><span class="sxs-lookup"><span data-stu-id="36cb5-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="36cb5-150">雖然必須有唯一的參數，針對每個參數集，參數可以屬於一個以上的參數集。</span><span class="sxs-lookup"><span data-stu-id="36cb5-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="36cb5-151">在這些情況下，授與共用的參數[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告，每個設定為此參數所屬。</span><span class="sxs-lookup"><span data-stu-id="36cb5-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="36cb5-152">如果參數是在所有的參數集，您只需要一次宣告的參數屬性，並不需要指定的參數集名稱。</span><span class="sxs-lookup"><span data-stu-id="36cb5-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="36cb5-153">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="36cb5-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="36cb5-154">每個 cmdlet 必須覆寫輸入處理方法，這是最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。</span><span class="sxs-lookup"><span data-stu-id="36cb5-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="36cb5-155">此 cmdlet，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ，讓此指令程式可以處理任意數目的處理程序，會覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="36cb5-155">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="36cb5-156">它包含哪些參數集的使用者不同的方法以呼叫已指定 Select 陳述式。</span><span class="sxs-lookup"><span data-stu-id="36cb5-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="36cb5-157">Select 陳述式所呼叫的 Helper 方法不在這裡詳述，但您可以查看其完整的程式碼範例下, 一節中的實作。</span><span class="sxs-lookup"><span data-stu-id="36cb5-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="36cb5-158">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="36cb5-158">Code Sample</span></span>

<span data-ttu-id="36cb5-159">完整C#程式碼範例，請參閱 < [StopProcessSample04 範例](./stopprocesssample04-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="36cb5-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="36cb5-160">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="36cb5-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="36cb5-161">Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="36cb5-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="36cb5-162">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="36cb5-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="36cb5-163">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="36cb5-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="36cb5-164">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="36cb5-164">Building the Cmdlet</span></span>

<span data-ttu-id="36cb5-165">在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="36cb5-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="36cb5-166">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="36cb5-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="36cb5-167">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="36cb5-167">Testing the Cmdlet</span></span>

<span data-ttu-id="36cb5-168">當尚未註冊 Windows PowerShell cmdlet 時，請執行命令列上測試。</span><span class="sxs-lookup"><span data-stu-id="36cb5-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="36cb5-169">以下是一些測試，顯示如何`ProcessId`和`InputObject`參數可用來測試其停止處理序的參數集。</span><span class="sxs-lookup"><span data-stu-id="36cb5-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="36cb5-170">啟動 Windows powershell 中，執行 停止處理序指令程式搭配`ProcessId`參數設定為停止處理程序根據其識別項。</span><span class="sxs-lookup"><span data-stu-id="36cb5-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="36cb5-171">在此情況下，使用此 cmdlet`ProcessId`參數設定為停止程序。</span><span class="sxs-lookup"><span data-stu-id="36cb5-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="36cb5-172">啟動 Windows powershell 中，執行 停止處理序指令程式搭配`InputObject`參數設定為停止處理程序所擷取的 「 記事本 」 物件上`Get-Process`命令。</span><span class="sxs-lookup"><span data-stu-id="36cb5-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="36cb5-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36cb5-173">See Also</span></span>

[<span data-ttu-id="36cb5-174">建立 Cmdlet 會修改系統</span><span class="sxs-lookup"><span data-stu-id="36cb5-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="36cb5-175">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="36cb5-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="36cb5-176">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="36cb5-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="36cb5-177">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="36cb5-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="36cb5-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="36cb5-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
