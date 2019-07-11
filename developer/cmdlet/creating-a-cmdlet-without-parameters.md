---
title: 建立不含參數的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733959"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="e8146-102">建立不含參數的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8146-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="e8146-103">本節說明如何建立 cmdlet 會從本機電腦，而不使用參數，擷取資訊，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="e8146-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="e8146-104">此處所述的 cmdlet 是 Get-proc cmdlet 會擷取本機電腦的處理序的相關資訊，然後在命令列中顯示這些資訊。</span><span class="sxs-lookup"><span data-stu-id="e8146-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="e8146-105">請注意，在撰寫 cmdlet，Windows PowerShell® 參考組件預設會下載到磁碟上 （位於 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。</span><span class="sxs-lookup"><span data-stu-id="e8146-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="e8146-106">它們不會安裝在全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="e8146-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="e8146-107">命名 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8146-107">Naming the Cmdlet</span></span>

<span data-ttu-id="e8146-108">Cmdlet 名稱是由，指出此 cmdlet 執行的動作動詞和名詞，指出此 cmdlet 作用的項目所組成。</span><span class="sxs-lookup"><span data-stu-id="e8146-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="e8146-109">由於此範例的 Get-proc cmdlet 擷取程序物件，它會使用動詞命令 「 取得 」，由[System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)列舉和名詞"Proc"來表示此指令程式，適用於程序項目。</span><span class="sxs-lookup"><span data-stu-id="e8146-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="e8146-110">在命名 cmdlet 時，請勿使用任何下列字元: #，（） {} [] &-/ \ $;:"' <>&#124;嗎？</span><span class="sxs-lookup"><span data-stu-id="e8146-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="e8146-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="e8146-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="e8146-112">選擇一個名詞</span><span class="sxs-lookup"><span data-stu-id="e8146-112">Choosing a Noun</span></span>

<span data-ttu-id="e8146-113">您應該選擇特定的名詞。</span><span class="sxs-lookup"><span data-stu-id="e8146-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="e8146-114">最好的方式是使用單數的名詞，加上一個精簡版本的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="e8146-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="e8146-115">此類型的範例指令程式名稱是"`Get-SQLServer`」。</span><span class="sxs-lookup"><span data-stu-id="e8146-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="e8146-116">選擇動詞命令</span><span class="sxs-lookup"><span data-stu-id="e8146-116">Choosing a Verb</span></span>

<span data-ttu-id="e8146-117">您應該使用的動詞命令，從一組核准的 cmdlet 動詞命令名稱。</span><span class="sxs-lookup"><span data-stu-id="e8146-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="e8146-118">如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="e8146-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="e8146-119">定義在 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="e8146-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="e8146-120">一旦您選擇的 cmdlet 名稱，定義.NET 類別來實作此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8146-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="e8146-121">以下是此範例的 Get-proc cmdlet 的類別定義：</span><span class="sxs-lookup"><span data-stu-id="e8146-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="e8146-122">請注意，類別定義之前[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性，且語法`[Cmdlet(verb, noun, ...)]`，用來識別此指令程式的類別。</span><span class="sxs-lookup"><span data-stu-id="e8146-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="e8146-123">這是唯一的必要的屬性，所有的 cmdlet，並可讓 Windows PowerShell 執行階段正確地呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="e8146-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="e8146-124">您可以設定屬性的關鍵字，以進一步在必要時在類別宣告。</span><span class="sxs-lookup"><span data-stu-id="e8146-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="e8146-125">請注意，我們的範例 GetProcCommand 類別的屬性宣告會宣告只有名詞與動詞名稱 Get-proc cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8146-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e8146-126">針對所有的 Windows PowerShell 屬性類別，您可以設定的關鍵字會對應至屬性類別的屬性中。</span><span class="sxs-lookup"><span data-stu-id="e8146-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="e8146-127">在命名類別指令程式時，最好以反映 cmdlet 名稱中的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="e8146-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="e8146-128">若要這樣做，請使用格式"VerbNounCommand"並取代 「 動詞 」 和 「 名詞 」 cmdlet 名稱中使用的名詞與動詞命令。</span><span class="sxs-lookup"><span data-stu-id="e8146-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="e8146-129">範例 Get-proc cmdlet 在先前的類別定義中所示定義一個叫做 GetProcCommand，衍生自類別[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基底類別。</span><span class="sxs-lookup"><span data-stu-id="e8146-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8146-130">如果您想要定義直接存取 Windows PowerShell 執行階段的 cmdlet，您的.NET 類別應該衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基底類別。</span><span class="sxs-lookup"><span data-stu-id="e8146-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="e8146-131">如需有關這個類別的詳細資訊，請參閱 <<c0> [ 該定義的參數集建立 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="e8146-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e8146-132">Cmdlet 類別必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="e8146-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="e8146-133">未標示為公用的類別會預設為內部，並且將找不到 Windows PowerShell 執行階段。</span><span class="sxs-lookup"><span data-stu-id="e8146-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="e8146-134">Windows PowerShell 會使用[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)其 cmdlet 類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e8146-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="e8146-135">建議將您的 API 命名空間，例如 xxx.PS.Commands 命令命名空間中的 cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="e8146-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e8146-136">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="e8146-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e8146-137">[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別提供三種主要的輸入的處理方法，至少一個 cmdlet 必須覆寫。</span><span class="sxs-lookup"><span data-stu-id="e8146-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="e8146-138">如需有關 Windows PowerShell 如何處理記錄的詳細資訊，請參閱 < [Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="e8146-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="e8146-139">針對所有類型的輸入，Windows PowerShell 執行階段會呼叫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)以便處理。</span><span class="sxs-lookup"><span data-stu-id="e8146-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="e8146-140">如果您的 cmdlet 都必須執行某些前置處理或安裝程式，它可以執行這項操作藉由覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="e8146-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="e8146-141">Windows PowerShell 會使用 「 記錄 」 這個詞彙來描述的一組 cmdlet 呼叫時提供的參數值。</span><span class="sxs-lookup"><span data-stu-id="e8146-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="e8146-142">如果您的 cmdlet 會接受管線輸入，則必須覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並選擇性地[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="e8146-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="e8146-143">比方說，cmdlet 可能會覆寫這兩種方法會收集所有的輸入使用如果[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)再作輸入為整體，而不是一個項目一次為`Sort-Object`cmdlet 會執行。</span><span class="sxs-lookup"><span data-stu-id="e8146-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="e8146-144">如果您的 cmdlet 不接受管線輸入，它應該覆寫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="e8146-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="e8146-145">請注意，這個方法經常用來取代[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)當 cmdlet 能用在上一個項目一次在此情況下，排序的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8146-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="e8146-146">此範例的 Get-proc cmdlet 必須接收管線輸入，因為它會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並使用的預設實作[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)並[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。</span><span class="sxs-lookup"><span data-stu-id="e8146-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="e8146-147">[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)覆寫擷取處理序，並將它們寫入命令列中使用[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。</span><span class="sxs-lookup"><span data-stu-id="e8146-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="e8146-148">有關輸入處理的注意事項</span><span class="sxs-lookup"><span data-stu-id="e8146-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="e8146-149">輸入的預設來源是在命令列上使用者所提供的明確物件 （例如，字串）。</span><span class="sxs-lookup"><span data-stu-id="e8146-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="e8146-150">如需詳細資訊，請參閱 <<c0> [ 建立可處理命令列輸入的 Cmdlet](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="e8146-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="e8146-151">處理方法的輸入也可以接收來自管線上游 cmdlet 的輸出物件的輸入。</span><span class="sxs-lookup"><span data-stu-id="e8146-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="e8146-152">如需詳細資訊，請參閱 <<c0> [ 建立可處理程序管線輸入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="e8146-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="e8146-153">請注意您的指令程式可以接收來自命令列組合的輸入和管線的來源。</span><span class="sxs-lookup"><span data-stu-id="e8146-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="e8146-154">長的時間，或根本不可能不會傳回下游的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8146-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="e8146-155">基於這個理由的輸入處理方法，在您的 cmdlet 不應保留的鎖定期間呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，特別是，範圍會延伸超出指令程式執行個體的鎖定。</span><span class="sxs-lookup"><span data-stu-id="e8146-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8146-156">指令程式應該永遠不會呼叫[System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine)或其對等項目。</span><span class="sxs-lookup"><span data-stu-id="e8146-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="e8146-157">您的 cmdlet 可能會有物件變數，以完成後清除處理 (例如，如果開啟檔案控制代碼，以[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，並維持控制代碼，已開啟供[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord))。</span><span class="sxs-lookup"><span data-stu-id="e8146-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="e8146-158">請務必記住，Windows PowerShell 執行階段不會一律呼叫[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，它應該執行物件的清除。</span><span class="sxs-lookup"><span data-stu-id="e8146-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="e8146-159">例如， [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)可能不會呼叫如果 cmdlet 會中途取消或終止錯誤發生在此指令程式的任何部分。</span><span class="sxs-lookup"><span data-stu-id="e8146-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="e8146-160">因此，需要物件清除 cmdlet 應該實作完整[System.IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，可讓執行階段呼叫兩者[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)並[System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose)結尾的處理。</span><span class="sxs-lookup"><span data-stu-id="e8146-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e8146-161">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e8146-161">Code Sample</span></span>

<span data-ttu-id="e8146-162">完整C#程式碼範例，請參閱 < [GetProcessSample01 範例](./getprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="e8146-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="e8146-163">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="e8146-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="e8146-164">Windows PowerShell cmdlet 使用.NET 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="e8146-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="e8146-165">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e8146-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e8146-166">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="e8146-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e8146-167">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="e8146-167">Building the Cmdlet</span></span>

<span data-ttu-id="e8146-168">在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e8146-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e8146-169">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="e8146-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e8146-170">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8146-170">Testing the Cmdlet</span></span>

<span data-ttu-id="e8146-171">當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="e8146-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e8146-172">我們的範例 Get-proc cmdlet 的程式碼很小，但是它仍然會使用 Windows PowerShell 執行階段和現有的.NET 物件，這就足以讓有用。</span><span class="sxs-lookup"><span data-stu-id="e8146-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="e8146-173">讓我們來測試它，以深入了解 Get-proc 可以做什麼，以及如何使用它的輸出。</span><span class="sxs-lookup"><span data-stu-id="e8146-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="e8146-174">如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="e8146-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="e8146-175">啟動 Windows PowerShell，並取得目前的處理程序在電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="e8146-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="e8146-176">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e8146-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="e8146-177">變數指派給 cmdlet 的結果更容易操作。</span><span class="sxs-lookup"><span data-stu-id="e8146-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="e8146-178">取得處理序數目。</span><span class="sxs-lookup"><span data-stu-id="e8146-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="e8146-179">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e8146-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="e8146-180">擷取特定的處理程序。</span><span class="sxs-lookup"><span data-stu-id="e8146-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="e8146-181">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e8146-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="e8146-182">取得這個處理程序的開始時間。</span><span class="sxs-lookup"><span data-stu-id="e8146-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="e8146-183">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e8146-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="e8146-184">取得控制代碼計數會大於 500，處理程序和排序結果。</span><span class="sxs-lookup"><span data-stu-id="e8146-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="e8146-185">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e8146-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="e8146-186">使用`Get-Member`cmdlet 來列出每個處理序可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="e8146-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="e8146-187">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e8146-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="e8146-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8146-188">See Also</span></span>

[<span data-ttu-id="e8146-189">建立可處理命令列輸入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8146-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="e8146-190">建立可處理管線輸入的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8146-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="e8146-191">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8146-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="e8146-192">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e8146-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="e8146-193">[Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e8146-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="e8146-194">[如何註冊 Cmdlet、 提供者，以及裝載應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e8146-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="e8146-195">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="e8146-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e8146-196">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="e8146-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)