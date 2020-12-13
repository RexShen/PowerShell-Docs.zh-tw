---
ms.date: 09/13/2016
ms.topic: reference
title: 新增處理命令列輸入的參數
description: 新增處理命令列輸入的參數
ms.openlocfilehash: f20469d366330aa787fbc16e4f0a76e67fc7c6db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354604"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="37307-103">新增處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="37307-103">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="37307-104">Cmdlet 的一個輸入來源是命令列。</span><span class="sxs-lookup"><span data-stu-id="37307-104">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="37307-105">本主題說明如何將參數新增至 Cmdlet， `Get-Proc` (在 [建立第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)) 中所述，讓 Cmdlet 可以根據傳遞給 Cmdlet 的明確物件，處理來自本機電腦的輸入。</span><span class="sxs-lookup"><span data-stu-id="37307-105">This topic describes how to add a parameter to the `Get-Proc` cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="37307-106">`Get-Proc`此處所述的 Cmdlet 會根據其名稱抓取程式，然後在命令提示字元中顯示處理常式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="37307-106">The `Get-Proc` cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="37307-107">定義 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="37307-107">Defining the Cmdlet Class</span></span>

<span data-ttu-id="37307-108">Cmdlet 建立的第一個步驟是 Cmdlet 的命名，以及用來執行 Cmdlet 之 .NET Framework 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="37307-108">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="37307-109">此 Cmdlet 會取出進程資訊，因此此處選擇的動詞名稱為 "Get"。</span><span class="sxs-lookup"><span data-stu-id="37307-109">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="37307-110"> (幾乎任何能夠抓取資訊的 Cmdlet 都可以處理命令列輸入 ) 。如需已核准的 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="37307-110">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="37307-111">以下是 Cmdlet 的類別宣告 `Get-Proc` 。</span><span class="sxs-lookup"><span data-stu-id="37307-111">Here's the class declaration for the `Get-Proc` cmdlet.</span></span> <span data-ttu-id="37307-112">[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)時，會提供有關此定義的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="37307-112">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="37307-113">宣告參數</span><span class="sxs-lookup"><span data-stu-id="37307-113">Declaring Parameters</span></span>

<span data-ttu-id="37307-114">Cmdlet 參數可讓使用者提供 Cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="37307-114">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="37307-115">在下列範例中， `Get-Proc` 和 `Get-Member` 是管線 Cmdlet 的名稱，而 `MemberType` 是 Cmdlet 的參數 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="37307-115">In the following example, `Get-Proc` and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="37307-116">參數有 "property" 引數。</span><span class="sxs-lookup"><span data-stu-id="37307-116">The parameter has the argument "property."</span></span>

<span data-ttu-id="37307-117">**PS> 的 get-proc; `get-member` -membertype 屬性**</span><span class="sxs-lookup"><span data-stu-id="37307-117">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="37307-118">若要宣告 Cmdlet 的參數，您必須先定義代表參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="37307-118">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="37307-119">在 `Get-Proc` 此 Cmdlet 中，唯一的參數是 `Name` ，在此案例中代表要抓取 .NET Framework 進程物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="37307-119">In the `Get-Proc` cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="37307-120">因此，Cmdlet 類別會定義字串類型的屬性，以接受名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="37307-120">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="37307-121">以下是 Cmdlet 參數的參數宣告 `Name` `Get-Proc` 。</span><span class="sxs-lookup"><span data-stu-id="37307-121">Here's the parameter declaration for the `Name` parameter of the `Get-Proc` cmdlet.</span></span>

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

<span data-ttu-id="37307-122">若要通知 Windows PowerShell 執行時間這個屬性是 `Name` 參數， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 屬性會加入至屬性定義。</span><span class="sxs-lookup"><span data-stu-id="37307-122">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="37307-123">宣告這個屬性的基本語法為 `[Parameter()]` 。</span><span class="sxs-lookup"><span data-stu-id="37307-123">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="37307-124">參數必須明確標記為公用。</span><span class="sxs-lookup"><span data-stu-id="37307-124">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="37307-125">未標記為 public 的參數預設為內部，且 Windows PowerShell 執行時間找不到這些參數。</span><span class="sxs-lookup"><span data-stu-id="37307-125">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="37307-126">此 Cmdlet 會使用參數的字串陣列 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="37307-126">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="37307-127">可能的話，您的 Cmdlet 也應該將參數定義為數組，因為這可讓 Cmdlet 接受一個以上的專案。</span><span class="sxs-lookup"><span data-stu-id="37307-127">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="37307-128">有關參數定義的注意事項</span><span class="sxs-lookup"><span data-stu-id="37307-128">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="37307-129">預先定義的 Windows PowerShell 參數名稱和資料類型應盡可能重複使用，以確保您的 Cmdlet 與 Windows PowerShell Cmdlet 相容。</span><span class="sxs-lookup"><span data-stu-id="37307-129">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="37307-130">例如，如果所有 Cmdlet 都使用預先定義的 `Id` 參數名稱來識別資源，則不論使用哪一個 Cmdlet，使用者都可以輕鬆地瞭解參數的意義。</span><span class="sxs-lookup"><span data-stu-id="37307-130">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="37307-131">基本上，參數名稱會遵循與在 common language runtime (CLR) 中用於變數名稱相同的規則。</span><span class="sxs-lookup"><span data-stu-id="37307-131">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="37307-132">如需參數命名的詳細資訊，請參閱 [Cmdlet 參數名稱](/previous-versions/ms714468(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="37307-132">For more information about parameter naming, see [Cmdlet Parameter Names](/previous-versions/ms714468(v=vs.85)).</span></span>

- <span data-ttu-id="37307-133">Windows PowerShell 會保留幾個參數名稱，以提供一致的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="37307-133">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="37307-134">請勿使用這些參數名稱： `WhatIf` 、 `Confirm` 、 `Verbose` 、 `Debug` 、 `Warn` 、、、 `ErrorAction` `ErrorVariable` `OutVariable` 和 `OutBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="37307-134">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="37307-135">此外，這些參數名稱的下列別名會保留： `vb` 、 `db` 、 `ea` 、 `ev` 、 `ov` 和 `ob` 。</span><span class="sxs-lookup"><span data-stu-id="37307-135">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="37307-136">`Name` 是簡單且一般的參數名稱，建議在您的 Cmdlet 中使用。</span><span class="sxs-lookup"><span data-stu-id="37307-136">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="37307-137">最好是選擇參數名稱，就像是特定 Cmdlet 唯一的複雜名稱一樣，而且難以記住。</span><span class="sxs-lookup"><span data-stu-id="37307-137">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="37307-138">Windows PowerShell 中的參數不區分大小寫，但根據預設，shell 會保留大小寫。</span><span class="sxs-lookup"><span data-stu-id="37307-138">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="37307-139">引數的區分大小寫取決於 Cmdlet 的操作。</span><span class="sxs-lookup"><span data-stu-id="37307-139">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="37307-140">引數會傳遞至命令列中指定的參數。</span><span class="sxs-lookup"><span data-stu-id="37307-140">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="37307-141">如需其他參數聲明的範例，請參閱 [Cmdlet 參數](./cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="37307-141">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="37307-142">將參數宣告為位置或命名</span><span class="sxs-lookup"><span data-stu-id="37307-142">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="37307-143">Cmdlet 必須將每個參數都設定為位置或具名引數。</span><span class="sxs-lookup"><span data-stu-id="37307-143">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="37307-144">這兩種參數都接受單一引數、多個以逗號分隔的引數，以及布林值設定。</span><span class="sxs-lookup"><span data-stu-id="37307-144">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="37307-145">布林值參數也稱為 *參數，只* 會處理布林值設定。</span><span class="sxs-lookup"><span data-stu-id="37307-145">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="37307-146">參數是用來判斷參數是否存在。</span><span class="sxs-lookup"><span data-stu-id="37307-146">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="37307-147">建議的預設值為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="37307-147">The recommended default is `false`.</span></span>

<span data-ttu-id="37307-148">範例 Cmdlet 會將 `Get-Proc` `Name` 參數定義為位置參數，並使用位置參數</span><span class="sxs-lookup"><span data-stu-id="37307-148">The sample `Get-Proc` cmdlet defines the `Name` parameter as a positional parameter with position</span></span>
0. <span data-ttu-id="37307-149">這表示，系統會自動為此參數插入使用者在命令列上輸入的第一個引數。</span><span class="sxs-lookup"><span data-stu-id="37307-149">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="37307-150">如果您想要定義一個具名引數，讓使用者必須從命令列指定參數名稱，請將 `Position` 關鍵字保留在屬性宣告之外。</span><span class="sxs-lookup"><span data-stu-id="37307-150">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="37307-151">除非參數必須命名，否則建議您將最常使用的參數設為位置，讓使用者不需要輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="37307-151">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="37307-152">將參數宣告為強制性或選擇性</span><span class="sxs-lookup"><span data-stu-id="37307-152">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="37307-153">Cmdlet 必須將每個參數設定為選擇性或強制參數。</span><span class="sxs-lookup"><span data-stu-id="37307-153">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="37307-154">在範例 `Get-Proc` Cmdlet 中， `Name` 參數定義為選擇性，因為屬性宣告 `Mandatory` 中未設定關鍵字。</span><span class="sxs-lookup"><span data-stu-id="37307-154">In the sample `Get-Proc` cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="37307-155">支援參數驗證</span><span class="sxs-lookup"><span data-stu-id="37307-155">Supporting Parameter Validation</span></span>

<span data-ttu-id="37307-156">範例 `Get-Proc` Cmdlet 會將輸入驗證屬性 [Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)新增至 `Name` 參數，以啟用輸入不是 `null` 或空白的驗證。</span><span class="sxs-lookup"><span data-stu-id="37307-156">The sample `Get-Proc` cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="37307-157">這個屬性是 Windows PowerShell 所提供的數個驗證屬性之一。</span><span class="sxs-lookup"><span data-stu-id="37307-157">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="37307-158">如需其他驗證屬性的範例，請參閱 [驗證參數輸入](./validating-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="37307-158">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="37307-159">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="37307-159">Overriding an Input Processing Method</span></span>

<span data-ttu-id="37307-160">如果您的 Cmdlet 是用來處理命令列輸入，則必須覆寫適當的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="37307-160">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="37307-161">基本輸入處理方法是在 [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)時引進。</span><span class="sxs-lookup"><span data-stu-id="37307-161">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="37307-162">此 `Get-Proc` Cmdlet 會覆寫 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法，以處理 `Name` 使用者或腳本提供的參數輸入。</span><span class="sxs-lookup"><span data-stu-id="37307-162">The `Get-Proc` cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="37307-163">這個方法會取得每個要求之進程名稱的處理常式，如果未提供任何名稱，則會取得所有的進程。</span><span class="sxs-lookup"><span data-stu-id="37307-163">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="37307-164">請注意，在 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中，呼叫 [WriteObject% 28system.string 29> .%. 布林值 %29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 是將輸出物件傳送至管線的輸出機制。（& a）</span><span class="sxs-lookup"><span data-stu-id="37307-164">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="37307-165">這個呼叫的第二個參數 `enumerateCollection` 會設為， `true` 以通知 Windows PowerShell 執行時間列舉處理常式物件的輸出陣列，並一次將一個進程寫入命令列。</span><span class="sxs-lookup"><span data-stu-id="37307-165">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="37307-166">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="37307-166">Code Sample</span></span>

<span data-ttu-id="37307-167">如需完整的 c # 範例程式碼，請參閱 [>getprocesssample02 範例](./getprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="37307-167">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="37307-168">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="37307-168">Defining Object Types and Formatting</span></span>

<span data-ttu-id="37307-169">Windows PowerShell 使用 .NET Framework 物件，在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="37307-169">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="37307-170">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="37307-170">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="37307-171">如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions/ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="37307-171">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="37307-172">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37307-172">Building the Cmdlet</span></span>

<span data-ttu-id="37307-173">在執行 Cmdlet 之後，您必須使用 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。</span><span class="sxs-lookup"><span data-stu-id="37307-173">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="37307-174">如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="37307-174">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="37307-175">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37307-175">Testing the Cmdlet</span></span>

<span data-ttu-id="37307-176">當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="37307-176">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="37307-177">以下是兩種測試範例 Cmdlet 程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="37307-177">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="37307-178">如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [消費者入門與 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="37307-178">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="37307-179">在 Windows PowerShell 提示字元中，使用下列命令來列出名為 "IEXPLORE.EXE" 的 Internet Explorer 進程。</span><span class="sxs-lookup"><span data-stu-id="37307-179">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

  ```powershell
  get-proc -name iexplore
  ```

  <span data-ttu-id="37307-180">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="37307-180">The following output appears.</span></span>

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- <span data-ttu-id="37307-181">若要列出名稱為 "IEXPLORE.EXE"、"OUTLOOK" 和 "NOTEPAD" 的 Internet Explorer、Outlook 和 Notepad 進程，請使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="37307-181">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="37307-182">如果有多個處理常式，則會顯示它們。</span><span class="sxs-lookup"><span data-stu-id="37307-182">If there are multiple processes, all of them are displayed.</span></span>

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  <span data-ttu-id="37307-183">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="37307-183">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a><span data-ttu-id="37307-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37307-184">See Also</span></span>

[<span data-ttu-id="37307-185">新增處理管道輸入的參數</span><span class="sxs-lookup"><span data-stu-id="37307-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="37307-186">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37307-186">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="37307-187">[擴充物件類型和格式化](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="37307-187">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="37307-188">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="37307-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="37307-189">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="37307-189">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="37307-190">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="37307-190">Cmdlet Samples</span></span>](./cmdlet-samples.md)
