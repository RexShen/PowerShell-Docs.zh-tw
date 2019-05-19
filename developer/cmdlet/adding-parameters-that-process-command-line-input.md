---
title: 將處理命令列輸入的參數加入 |Microsoft Docs
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
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854957"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="a0b8c-102">新增處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="a0b8c-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="a0b8c-103">其中一個的 cmdlet 來源是輸入的命令列。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="a0b8c-104">本主題描述如何將參數加入**Get-proc** cmdlet (見[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))，讓此指令程式可以處理從明確為基礎的本機電腦的輸入物件會傳遞至 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="a0b8c-105">**Get-proc**這裡擷取其名稱為基礎的處理序所述的 cmdlet，並接著會處理序的相關資訊顯示在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="a0b8c-106">定義在 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="a0b8c-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="a0b8c-107">Cmdlet 建立的第一個步驟是，cmdlet 命名並實作指令程式的.NET Framework 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="a0b8c-108">此 cmdlet 可擷取處理序資訊，所以在這裡選擇的指令動詞名稱是 「 取得 」。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="a0b8c-109">（幾乎任何一種能夠擷取資訊的指令程式可以處理命令列輸入）。如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="a0b8c-110">以下是類別宣告**Get-proc** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="a0b8c-111">將提供關於此定義的詳細資料[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="a0b8c-112">宣告參數</span><span class="sxs-lookup"><span data-stu-id="a0b8c-112">Declaring Parameters</span></span>

<span data-ttu-id="a0b8c-113">Cmdlet 參數可讓使用者提供 cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="a0b8c-114">在下列範例中， **Get-proc**並`Get-Member`是導送 cmdlet 的名稱並`MemberType`是參數`Get-Member`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="a0b8c-115">參數的引數"property"。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="a0b8c-116">**PS > 取得跨處理序;`get-member` -membertype 屬性**</span><span class="sxs-lookup"><span data-stu-id="a0b8c-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="a0b8c-117">若要宣告 cmdlet 的參數，您必須先定義代表參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="a0b8c-118">在  **Get-proc** cmdlet，唯一的參數是`Name`，在此情況下代表要擷取之.NET Framework 程序物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="a0b8c-119">因此，在 cmdlet 類別定義接受名稱的陣列的字串類型屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="a0b8c-120">以下是參數宣告`Name`的參數**Get-proc** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="a0b8c-121">若要通知，這個值，Windows PowerShell 執行階段`Name`參數， [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性加入至屬性定義。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="a0b8c-122">宣告這個屬性的基本語法是`[Parameter()]`。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="a0b8c-123">參數必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="a0b8c-124">未標示為公用的預設值為 internal，和 Windows PowerShell 執行階段找不到的參數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="a0b8c-125">此 cmdlet 會使用字串的陣列`Name`參數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="a0b8c-126">可能的話，您的 cmdlet 也應該定義參數陣列，因為這可讓 cmdlet 接受一個以上的項目。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="a0b8c-127">參數定義時，必須注意的事項</span><span class="sxs-lookup"><span data-stu-id="a0b8c-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="a0b8c-128">預先定義的 Windows PowerShell 參數名稱和資料類型應該重複使用盡量確保您的 cmdlet 與 Windows PowerShell cmdlet 相容。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="a0b8c-129">例如，如果使用預先定義的所有 cmdlet`Id`參數名稱來識別資源，使用者可輕鬆地了解參數，無論他們使用何種 cmdlet 的意義。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="a0b8c-130">基本上，參數名稱會遵循相同的規則所使用的 common language runtime (CLR) 中的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="a0b8c-131">如需參數命名的詳細資訊，請參閱[Cmdlet 的參數名稱](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="a0b8c-132">Windows PowerShell 會保留幾個參數名稱，以提供一致的使用者體驗。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="a0b8c-133">請勿使用這些參數名稱： `WhatIf`， `Confirm`， `Verbose`， `Debug`， `Warn`， `ErrorAction`， `ErrorVariable`， `OutVariable`，和`OutBuffer`。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="a0b8c-134">此外，保留了這些參數名稱的下列別名： `vb`， `db`， `ea`， `ev`， `ov`，和`ob`。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="a0b8c-135">`Name` 是簡單且常見的參數名稱，建議在您的 cmdlet 中使用。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="a0b8c-136">您最好選擇比特定指令程式所特有而且難以記住複雜名稱如下的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="a0b8c-137">參數是在 Windows PowerShell 中，不區分大小寫的雖然預設殼層會保留大小寫。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="a0b8c-138">引數的區分大小寫取決於此指令程式的作業。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="a0b8c-139">引數會指定在命令列傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="a0b8c-140">如需其他的參數宣告的範例，請參閱[Cmdlet 參數](./cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="a0b8c-141">宣告為位置或具名的參數</span><span class="sxs-lookup"><span data-stu-id="a0b8c-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="a0b8c-142">指令程式必須設定每個參數為位置或具名參數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="a0b8c-143">這兩種參數接受單一引數，並以逗號和布林設定分隔的多個引數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="a0b8c-144">布林值的參數，也稱為*切換*，處理，則為 True 的設定。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="a0b8c-145">參數用來判斷參數存在。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="a0b8c-146">建議的預設值是`false`。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-146">The recommended default is `false`.</span></span>

<span data-ttu-id="a0b8c-147">此範例**Get-proc** cmdlet 定義`Name`參數做為位置參數，以位置為 0。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="a0b8c-148">這表示使用者輸入的命令列的第一個引數會自動插入這個參數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="a0b8c-149">如果您想要定義具名的參數，使用者必須指定參數名稱從命令列中，將保留`Position`從屬性宣告的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="a0b8c-150">除非必須命名參數，否則我們建議您最常使用的參數位置，讓使用者不需要輸入參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="a0b8c-151">宣告為強制或選擇性的參數</span><span class="sxs-lookup"><span data-stu-id="a0b8c-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="a0b8c-152">指令程式必須設定每個參數為選擇性或必要的參數。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="a0b8c-153">在此範例中**Get-proc** cmdlet，此 cmdlet`Name`參數會定義為選擇性，因為`Mandatory`屬性宣告中未設定關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="a0b8c-154">支援的參數驗證</span><span class="sxs-lookup"><span data-stu-id="a0b8c-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="a0b8c-155">此範例**Get-proc** cmdlet 會將輸入的驗證屬性 (attribute) [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)至`Name`參數，以啟用驗證，既不是輸入`null`或空白。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="a0b8c-156">這個屬性是其中一個 Windows PowerShell 所提供的數個驗證屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="a0b8c-157">如需其他的驗證屬性的範例，請參閱[驗證參數輸入](./validating-parameter-input.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="a0b8c-158">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="a0b8c-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="a0b8c-159">如果您的指令程式來處理命令列輸入，它必須覆寫適當的輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="a0b8c-160">在中引進的基本輸入的處理方法[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="a0b8c-161">**Get-proc** cmdlet 會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理`Name`使用者或指令碼所提供的參數輸入。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="a0b8c-162">如果未提供名稱，這個方法會取得每個要求的處理序名稱，或所有處理序的處理程序。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="a0b8c-163">請注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，來呼叫[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)是輸出機制，將輸出傳送到管線的物件。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="a0b8c-164">此呼叫中，第二個參數`enumerateCollection`，設定為`true`告知 Windows PowerShell 執行階段列舉的處理程序物件的輸出陣列和一個處理序一次寫入命令列。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="a0b8c-165">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a0b8c-165">Code Sample</span></span>

<span data-ttu-id="a0b8c-166">完整C#程式碼範例，請參閱 < [GetProcessSample02 範例](./getprocesssample02-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="a0b8c-167">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="a0b8c-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="a0b8c-168">Windows PowerShell cmdlet，使用.NET Framework 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="a0b8c-169">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="a0b8c-170">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="a0b8c-171">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="a0b8c-171">Building the Cmdlet</span></span>

<span data-ttu-id="a0b8c-172">您實作的 cmdlet 之後，您必須使用 Windows PowerShell 註冊使用 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="a0b8c-173">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="a0b8c-174">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0b8c-174">Testing the Cmdlet</span></span>

<span data-ttu-id="a0b8c-175">使用 Windows PowerShell 註冊您的 cmdlet 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="a0b8c-176">以下是兩種方式可以測試此範例指令程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="a0b8c-177">如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="a0b8c-178">在 Windows PowerShell 提示字元中，使用下列命令來列出 Internet Explorer 的程序，名為"IEXPLORE。 」</span><span class="sxs-lookup"><span data-stu-id="a0b8c-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="a0b8c-179">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="a0b8c-180">若要列出的 Internet Explorer、 Outlook 和 「 記事本 」 處理程序名為"IEXPLORE"，"OUTLOOK"和"NOTEPAD，"使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="a0b8c-181">如果有多個處理序，其中會顯示所有。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="a0b8c-182">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a0b8c-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="a0b8c-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b8c-183">See Also</span></span>

[<span data-ttu-id="a0b8c-184">新增處理程序管線輸入的參數</span><span class="sxs-lookup"><span data-stu-id="a0b8c-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="a0b8c-185">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0b8c-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="a0b8c-186">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="a0b8c-186">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="a0b8c-187">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="a0b8c-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="a0b8c-188">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="a0b8c-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="a0b8c-189">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="a0b8c-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
