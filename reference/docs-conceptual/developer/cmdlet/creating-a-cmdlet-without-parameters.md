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
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415664"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="70531-102">建立不含參數的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70531-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="70531-103">本節說明如何建立在不使用參數的情況下，從本機電腦抓取資訊的 Cmdlet，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="70531-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="70531-104">這裡所述的 Cmdlet 是一個可抓取本機電腦處理常式相關資訊的 Get-Proc Cmdlet，然後在命令列中顯示該資訊。</span><span class="sxs-lookup"><span data-stu-id="70531-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="70531-105">請注意，在撰寫 Cmdlet 時，Windows PowerShell®參考元件會下載到磁片上（預設為 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。</span><span class="sxs-lookup"><span data-stu-id="70531-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="70531-106">它們不會安裝在全域組件快取（GAC）中。</span><span class="sxs-lookup"><span data-stu-id="70531-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="70531-107">命名 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70531-107">Naming the Cmdlet</span></span>

<span data-ttu-id="70531-108">Cmdlet 名稱是由指示 Cmdlet 所採取之動作的動詞，以及表示此 Cmdlet 作用之專案的名詞所組成。</span><span class="sxs-lookup"><span data-stu-id="70531-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="70531-109">因為此範例的 Get 程式 Cmdlet 會抓取進程物件，所以它會使用動詞命令 "Get" （由[Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)列舉所定義）和名詞 "Proc"，表示此 Cmdlet 適用于處理常式專案。</span><span class="sxs-lookup"><span data-stu-id="70531-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="70531-110">命名 Cmdlet 時，請勿使用下列任何字元： #、（） {} [] &-/\ $;： "' < > &#124;嗎？</span><span class="sxs-lookup"><span data-stu-id="70531-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="70531-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="70531-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="70531-112">選擇名詞</span><span class="sxs-lookup"><span data-stu-id="70531-112">Choosing a Noun</span></span>

<span data-ttu-id="70531-113">您應該選擇特定的名詞。</span><span class="sxs-lookup"><span data-stu-id="70531-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="70531-114">最好是使用前面加上產品名稱之縮寫版本的單數名詞。</span><span class="sxs-lookup"><span data-stu-id="70531-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="70531-115">此類型的範例 Cmdlet 名稱是 "`Get-SQLServer`"。</span><span class="sxs-lookup"><span data-stu-id="70531-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="70531-116">選擇動詞</span><span class="sxs-lookup"><span data-stu-id="70531-116">Choosing a Verb</span></span>

<span data-ttu-id="70531-117">您應該使用一組已核准的 Cmdlet 動詞名稱中的動詞。</span><span class="sxs-lookup"><span data-stu-id="70531-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="70531-118">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="70531-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="70531-119">定義 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="70531-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="70531-120">選擇 Cmdlet 名稱之後，請定義 .NET 類別來執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="70531-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="70531-121">以下是此範例 Get-Proc Cmdlet 的類別定義：</span><span class="sxs-lookup"><span data-stu-id="70531-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="70531-122">請注意，在類別定義之前，使用語法 `[Cmdlet(verb, noun, ...)]`的[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)屬性，是用來將此類別識別為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="70531-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="70531-123">這是所有 Cmdlet 唯一必要的屬性，它可讓 Windows PowerShell 執行時間正確地呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="70531-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="70531-124">您可以設定屬性關鍵字，以便在必要時進一步宣告類別。</span><span class="sxs-lookup"><span data-stu-id="70531-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="70531-125">請注意，我們的範例 GetProcCommand 類別的屬性宣告只會宣告 Get-help Cmdlet 的名詞和動詞名稱。</span><span class="sxs-lookup"><span data-stu-id="70531-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="70531-126">對於所有的 Windows PowerShell 屬性類別，您可以設定的關鍵字會對應到屬性類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="70531-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="70531-127">命名 Cmdlet 的類別時，最好是在類別名稱中反映 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="70531-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="70531-128">若要這麼做，請使用 "VerbNounCommand" 格式，並將 "Verb" 和 "名詞" 取代為 Cmdlet 名稱中使用的動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="70531-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="70531-129">如先前的類別定義中所示，範例 Get-Proc Cmdlet 會定義名為 GetProcCommand 的類別，其衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)基類。</span><span class="sxs-lookup"><span data-stu-id="70531-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70531-130">如果您想要定義直接存取 Windows PowerShell 執行時間的 Cmdlet，您的 .NET 類別應該衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基類。</span><span class="sxs-lookup"><span data-stu-id="70531-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="70531-131">如需此類別的詳細資訊，請參閱[建立定義參數集的 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="70531-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="70531-132">Cmdlet 的類別必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="70531-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="70531-133">未標示為公用的類別會預設為內部，且不會由 Windows PowerShell 執行時間找到。</span><span class="sxs-lookup"><span data-stu-id="70531-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="70531-134">Windows PowerShell 會針對其 Cmdlet 類別使用[Microsoft. powershell. 命令](/dotnet/api/Microsoft.PowerShell.Commands)命名空間。</span><span class="sxs-lookup"><span data-stu-id="70531-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="70531-135">建議您將 Cmdlet 類別放在 API 命名空間的命令命名空間中，例如 xxx. PS. 命令。</span><span class="sxs-lookup"><span data-stu-id="70531-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="70531-136">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="70531-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="70531-137">[System.web](/dotnet/api/System.Management.Automation.Cmdlet)類別提供三種主要的輸入處理方法，其中至少有一個 Cmdlet 必須覆寫。</span><span class="sxs-lookup"><span data-stu-id="70531-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="70531-138">如需 Windows PowerShell 如何處理記錄的詳細資訊，請參閱[Windows powershell 的運作方式](/previous-versions//ms714658(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="70531-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="70531-139">針對所有類型的輸入，Windows PowerShell 執行時間會呼叫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)以啟用處理。</span><span class="sxs-lookup"><span data-stu-id="70531-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="70531-140">如果您的 Cmdlet 必須執行一些前置處理或設定，可以藉由覆寫此方法來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="70531-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="70531-141">Windows PowerShell 使用「記錄」一詞來描述呼叫 Cmdlet 時所提供的參數值集。</span><span class="sxs-lookup"><span data-stu-id="70531-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="70531-142">如果您的 Cmdlet 接受管線輸入，它就必須覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並選擇性地覆寫[system.servicemodel 方法和。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)</span><span class="sxs-lookup"><span data-stu-id="70531-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="70531-143">例如，Cmdlet 可能會覆寫這兩個方法（如果它會使用[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)來收集所有輸入），然後一次在輸入上當做整體而不是一個元素來操作，如同 `Sort-Object` Cmdlet 一樣。</span><span class="sxs-lookup"><span data-stu-id="70531-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="70531-144">如果您的 Cmdlet 不接受管線輸入，它應該覆寫[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。</span><span class="sxs-lookup"><span data-stu-id="70531-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="70531-145">請注意，當 Cmdlet 一次無法在一個專案上操作時，通常會使用這個方法來取代[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ，這就是排序 Cmdlet 的情況。</span><span class="sxs-lookup"><span data-stu-id="70531-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="70531-146">因為此範例過程指令程式必須接收管線輸入，所以它會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，並使用 BeginProcessing 和[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)的預設實作為檔案的管理[元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)（可能為系統管理）。</span><span class="sxs-lookup"><span data-stu-id="70531-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="70531-147">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)覆寫會抓取進程，並使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法將它們寫入至命令列中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="70531-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="70531-148">輸入處理需要注意的事項</span><span class="sxs-lookup"><span data-stu-id="70531-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="70531-149">輸入的預設來源是使用者在命令列上提供的明確物件（例如字串）。</span><span class="sxs-lookup"><span data-stu-id="70531-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="70531-150">如需詳細資訊，請參閱[建立 Cmdlet 來處理命令列輸入](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="70531-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="70531-151">輸入處理方法也可以從管線上上游 Cmdlet 的輸出物件接收輸入。</span><span class="sxs-lookup"><span data-stu-id="70531-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="70531-152">如需詳細資訊，請參閱[建立 Cmdlet 來處理管線輸入](./adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="70531-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="70531-153">請注意，您的 Cmdlet 可以從命令列和管線來源的組合接收輸入。</span><span class="sxs-lookup"><span data-stu-id="70531-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="70531-154">下游 Cmdlet 可能不會傳回長時間，或根本不會傳回。</span><span class="sxs-lookup"><span data-stu-id="70531-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="70531-155">基於這個理由，您 Cmdlet 中的輸入處理方法不應在呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)時保留鎖定，尤其是範圍延伸超過 Cmdlet 實例的鎖定。</span><span class="sxs-lookup"><span data-stu-id="70531-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70531-156">Cmdlet 絕對不應呼叫[system.object \*](/dotnet/api/System.Console.WriteLine)或其對等的。</span><span class="sxs-lookup"><span data-stu-id="70531-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="70531-157">當程式完成處理時，您的 Cmdlet 可能會有要清除的物件變數（例如，如果它在[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中開啟檔案控制代碼，並讓控制碼保持開啟以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)使用）。</span><span class="sxs-lookup"><span data-stu-id="70531-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="70531-158">請務必記住，Windows PowerShell 執行時間不一定會呼叫[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，這應該會執行物件清除。</span><span class="sxs-lookup"><span data-stu-id="70531-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="70531-159">例如，如果指令程式中途取消，或 Cmdlet 的任何部分發生終止錯誤，則可能不會呼叫[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 。</span><span class="sxs-lookup"><span data-stu-id="70531-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="70531-160">因此，需要物件清理的 Cmdlet 應該會執行完整的[IDisposable](/dotnet/api/System.IDisposable)模式，包括完成項，讓執行時間可以在處理結束時同時呼叫[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)和[IDisposable. Dispose \*](/dotnet/api/System.IDisposable.Dispose)程式。</span><span class="sxs-lookup"><span data-stu-id="70531-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="70531-161">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="70531-161">Code Sample</span></span>

<span data-ttu-id="70531-162">如需完整C#的範例程式碼，請參閱[GetProcessSample01 範例](./getprocesssample01-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="70531-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="70531-163">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="70531-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="70531-164">Windows PowerShell 會使用 .NET 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="70531-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="70531-165">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="70531-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="70531-166">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="70531-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="70531-167">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70531-167">Building the Cmdlet</span></span>

<span data-ttu-id="70531-168">在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="70531-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="70531-169">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="70531-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="70531-170">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70531-170">Testing the Cmdlet</span></span>

<span data-ttu-id="70531-171">當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="70531-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="70531-172">範例 Proc Cmdlet 的程式碼很小，但它仍會使用 Windows PowerShell 執行時間和現有的 .NET 物件，這足以讓它發揮作用。</span><span class="sxs-lookup"><span data-stu-id="70531-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="70531-173">讓我們來測試它，以進一步瞭解有哪些程式可執行，以及如何使用其輸出。</span><span class="sxs-lookup"><span data-stu-id="70531-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="70531-174">如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="70531-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="70531-175">啟動 Windows PowerShell，並取得電腦上正在執行的目前進程。</span><span class="sxs-lookup"><span data-stu-id="70531-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="70531-176">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70531-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="70531-177">將變數指派給 Cmdlet 結果，以方便操作。</span><span class="sxs-lookup"><span data-stu-id="70531-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="70531-178">取得進程的數目。</span><span class="sxs-lookup"><span data-stu-id="70531-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="70531-179">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70531-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="70531-180">取出特定的進程。</span><span class="sxs-lookup"><span data-stu-id="70531-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="70531-181">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70531-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="70531-182">取得此程式的開始時間。</span><span class="sxs-lookup"><span data-stu-id="70531-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="70531-183">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70531-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="70531-184">取得控制碼計數大於500的進程，並將結果排序。</span><span class="sxs-lookup"><span data-stu-id="70531-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="70531-185">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70531-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="70531-186">使用 `Get-Member` Cmdlet 來列出每個進程可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="70531-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="70531-187">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="70531-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="70531-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70531-188">See Also</span></span>

[<span data-ttu-id="70531-189">建立 Cmdlet 來處理命令列輸入</span><span class="sxs-lookup"><span data-stu-id="70531-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="70531-190">建立 Cmdlet 來處理管線輸入</span><span class="sxs-lookup"><span data-stu-id="70531-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="70531-191">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70531-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="70531-192">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="70531-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="70531-193">[Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="70531-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="70531-194">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="70531-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="70531-195">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="70531-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="70531-196">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="70531-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
