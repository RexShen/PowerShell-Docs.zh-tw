---
title: 加入處理命令列輸入的參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364627"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="2292f-102">新增處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="2292f-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="2292f-103">Cmdlet 的輸入的其中一個來源是命令列。</span><span class="sxs-lookup"><span data-stu-id="2292f-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="2292f-104">本主題說明如何將參數新增至**get-help** Cmdlet （如[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)中所述），讓 Cmdlet 可以根據傳遞給 Cmdlet 的明確物件，處理本機電腦的輸入。</span><span class="sxs-lookup"><span data-stu-id="2292f-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="2292f-105">這裡所述的**get-help** Cmdlet 會根據其名稱來抓取進程，然後在命令提示字元中顯示進程的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2292f-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="2292f-106">定義 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="2292f-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="2292f-107">Cmdlet 建立的第一個步驟是 Cmdlet 命名，以及可執行 Cmdlet 之 .NET Framework 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="2292f-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="2292f-108">此 Cmdlet 會抓取處理常式資訊，因此此處選擇的動詞名稱是「Get」。</span><span class="sxs-lookup"><span data-stu-id="2292f-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="2292f-109">（幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入）。如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="2292f-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="2292f-110">以下是**get-help** Cmdlet 的類別宣告。</span><span class="sxs-lookup"><span data-stu-id="2292f-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="2292f-111">[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)時，會提供有關此定義的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2292f-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="2292f-112">宣告參數</span><span class="sxs-lookup"><span data-stu-id="2292f-112">Declaring Parameters</span></span>

<span data-ttu-id="2292f-113">Cmdlet 參數可讓使用者提供 Cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="2292f-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="2292f-114">在下列範例中， **Proc**和 `Get-Member` 是管線 Cmdlet 的名稱，而 `MemberType` 是 `Get-Member` Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="2292f-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="2292f-115">參數的引數為 "property"。</span><span class="sxs-lookup"><span data-stu-id="2292f-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="2292f-116">**PS > get 進程;`get-member` membertype 屬性**</span><span class="sxs-lookup"><span data-stu-id="2292f-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="2292f-117">若要宣告 Cmdlet 的參數，必須先定義代表參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="2292f-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="2292f-118">在**Get-Proc** Cmdlet 中，唯一的參數是 `Name`，在此案例中代表要抓取 .NET Framework 進程物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="2292f-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="2292f-119">因此，Cmdlet 類別會定義字串類型的屬性，以接受名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="2292f-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="2292f-120">以下是**get-help** Cmdlet 之 `Name` 參數的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="2292f-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="2292f-121">為了通知 Windows PowerShell 執行時間此屬性為 `Name` 參數，會將[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性新增至屬性定義。</span><span class="sxs-lookup"><span data-stu-id="2292f-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="2292f-122">`[Parameter()]`宣告這個屬性的基本語法。</span><span class="sxs-lookup"><span data-stu-id="2292f-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="2292f-123">參數必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="2292f-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="2292f-124">未標示為公用的參數預設為內部，Windows PowerShell 執行時間找不到。</span><span class="sxs-lookup"><span data-stu-id="2292f-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="2292f-125">此 Cmdlet 會使用 `Name` 參數的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="2292f-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="2292f-126">可能的話，您的 Cmdlet 也應該將參數定義為數組，因為這可讓 Cmdlet 接受一個以上的專案。</span><span class="sxs-lookup"><span data-stu-id="2292f-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="2292f-127">參數定義需要注意的事項</span><span class="sxs-lookup"><span data-stu-id="2292f-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="2292f-128">預先定義的 Windows PowerShell 參數名稱和資料類型應該盡可能重複使用，以確保您的 Cmdlet 與 Windows PowerShell Cmdlet 相容。</span><span class="sxs-lookup"><span data-stu-id="2292f-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="2292f-129">例如，如果所有 Cmdlet 都使用預先定義的 `Id` 參數名稱來識別資源，則無論參數的用途為何，使用者都能輕易地瞭解其意義。</span><span class="sxs-lookup"><span data-stu-id="2292f-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="2292f-130">基本上，參數名稱會遵循 common language runtime （CLR）中用於變數名稱的相同規則。</span><span class="sxs-lookup"><span data-stu-id="2292f-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="2292f-131">如需參數命名的詳細資訊，請參閱[Cmdlet 參數名稱](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)。</span><span class="sxs-lookup"><span data-stu-id="2292f-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="2292f-132">Windows PowerShell 會保留幾個參數名稱，以提供一致的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="2292f-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="2292f-133">請勿使用這些參數名稱： `WhatIf`、`Confirm`、`Verbose`、`Debug`、`Warn`、`ErrorAction`、`ErrorVariable`、`OutVariable`和 `OutBuffer`。</span><span class="sxs-lookup"><span data-stu-id="2292f-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="2292f-134">此外，系統會保留這些參數名稱的下列別名： `vb`、`db`、`ea`、`ev`、`ov`和 `ob`。</span><span class="sxs-lookup"><span data-stu-id="2292f-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="2292f-135">`Name` 是簡單且通用的參數名稱，建議您在 Cmdlet 中使用。</span><span class="sxs-lookup"><span data-stu-id="2292f-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="2292f-136">最好是選擇與特定指令程式特有的參數名稱，而不是特殊的名稱，因此很難記住。</span><span class="sxs-lookup"><span data-stu-id="2292f-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="2292f-137">在 Windows PowerShell 中，參數不區分大小寫，但根據預設，shell 會保留大小寫。</span><span class="sxs-lookup"><span data-stu-id="2292f-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="2292f-138">引數的區分大小寫取決於 Cmdlet 的作業。</span><span class="sxs-lookup"><span data-stu-id="2292f-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="2292f-139">引數會傳遞至命令列所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="2292f-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="2292f-140">如需其他參數宣告的範例，請參閱[Cmdlet 參數](./cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2292f-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="2292f-141">將參數宣告為位置或名稱</span><span class="sxs-lookup"><span data-stu-id="2292f-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="2292f-142">Cmdlet 必須將每個參數設定為位置或具名引數。</span><span class="sxs-lookup"><span data-stu-id="2292f-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="2292f-143">這兩種參數都接受單一引數、以逗號分隔的多個引數，以及布林值設定。</span><span class="sxs-lookup"><span data-stu-id="2292f-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="2292f-144">布林值參數（也稱為「*切換*」）只會處理布林值設定。</span><span class="sxs-lookup"><span data-stu-id="2292f-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="2292f-145">參數是用來判斷參數是否存在。</span><span class="sxs-lookup"><span data-stu-id="2292f-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="2292f-146">建議的預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2292f-146">The recommended default is `false`.</span></span>

<span data-ttu-id="2292f-147">範例**Get-Proc** Cmdlet 會將 `Name` 參數定義為位置參數，其位置為0。</span><span class="sxs-lookup"><span data-stu-id="2292f-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="2292f-148">這表示會自動為此參數插入使用者在命令列上輸入的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="2292f-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="2292f-149">如果您想要定義名為的參數（使用者必須從命令列指定參數名稱），請將 `Position` 關鍵字保留在屬性宣告之外。</span><span class="sxs-lookup"><span data-stu-id="2292f-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="2292f-150">除非參數必須命名，否則建議您將最常使用的參數設為位置，讓使用者不需要輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="2292f-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="2292f-151">將參數宣告為強制或選擇性</span><span class="sxs-lookup"><span data-stu-id="2292f-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="2292f-152">Cmdlet 必須將每個參數設定為選擇性或強制參數。</span><span class="sxs-lookup"><span data-stu-id="2292f-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="2292f-153">在範例**Get-Proc** Cmdlet 中，`Name` 參數定義為選擇性，因為屬性宣告中未設定 `Mandatory` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2292f-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="2292f-154">支援參數驗證</span><span class="sxs-lookup"><span data-stu-id="2292f-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="2292f-155">範例 [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)**指令程式會**將輸入驗證屬性（attribute） 新增至`Name`參數，以啟用輸入不是`null`也不是空的驗證。</span><span class="sxs-lookup"><span data-stu-id="2292f-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="2292f-156">此屬性是 Windows PowerShell 所提供的數個驗證屬性之一。</span><span class="sxs-lookup"><span data-stu-id="2292f-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="2292f-157">如需其他驗證屬性的範例，請參閱[驗證參數輸入](./validating-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="2292f-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="2292f-158">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="2292f-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="2292f-159">如果您的 Cmdlet 是用來處理命令列輸入，它必須覆寫適當的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="2292f-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="2292f-160">基本輸入處理方法會在[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)中引進。</span><span class="sxs-lookup"><span data-stu-id="2292f-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="2292f-161">**Get-help** Cmdlet 會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理使用者或腳本所提供的 `Name` 的參數輸入。</span><span class="sxs-lookup"><span data-stu-id="2292f-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="2292f-162">這個方法會取得每個要求之進程名稱的進程，如果未提供任何名稱，則為所有進程。</span><span class="sxs-lookup"><span data-stu-id="2292f-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="2292f-163">請注意，在[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中，對[WriteObject% 28system.string 29> 的呼叫。布林值 %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)是將輸出物件傳送至管線所用的輸出機制（output）。</span><span class="sxs-lookup"><span data-stu-id="2292f-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="2292f-164">此呼叫的第二個參數（`enumerateCollection`）會設定為 `true`，以通知 Windows PowerShell 執行時間列舉處理常式物件的輸出陣列，並一次將一個進程寫入命令列。</span><span class="sxs-lookup"><span data-stu-id="2292f-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="2292f-165">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="2292f-165">Code Sample</span></span>

<span data-ttu-id="2292f-166">如需完整C#的範例程式碼，請參閱[GetProcessSample02 範例](./getprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="2292f-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="2292f-167">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="2292f-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="2292f-168">Windows PowerShell 會使用 .NET Framework 物件，在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="2292f-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="2292f-169">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="2292f-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="2292f-170">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="2292f-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="2292f-171">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2292f-171">Building the Cmdlet</span></span>

<span data-ttu-id="2292f-172">執行 Cmdlet 之後，您必須使用 Windows PowerShell 嵌入式管理單元，向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="2292f-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="2292f-173">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="2292f-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="2292f-174">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2292f-174">Testing the Cmdlet</span></span>

<span data-ttu-id="2292f-175">當您的 Cmdlet 向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="2292f-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="2292f-176">以下兩種方式可以測試範例 Cmdlet 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2292f-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="2292f-177">如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="2292f-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="2292f-178">在 Windows PowerShell 提示字元中，使用下列命令來列出 Internet Explorer 進程（名為 "IEXPLORE.EXE"）。</span><span class="sxs-lookup"><span data-stu-id="2292f-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="2292f-179">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2292f-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="2292f-180">若要列出名為「IEXPLORE.EXE」、「OUTLOOK」和「記事本」的 Internet Explorer、Outlook 和記事本進程，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="2292f-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="2292f-181">如果有多個處理常式，則會顯示所有進程。</span><span class="sxs-lookup"><span data-stu-id="2292f-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="2292f-182">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="2292f-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="2292f-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2292f-183">See Also</span></span>

[<span data-ttu-id="2292f-184">加入處理管線輸入的參數</span><span class="sxs-lookup"><span data-stu-id="2292f-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="2292f-185">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2292f-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="2292f-186">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="2292f-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="2292f-187">如何註冊 Cmdlet、提供者和主機應用程式</span><span class="sxs-lookup"><span data-stu-id="2292f-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="2292f-188">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="2292f-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="2292f-189">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="2292f-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
