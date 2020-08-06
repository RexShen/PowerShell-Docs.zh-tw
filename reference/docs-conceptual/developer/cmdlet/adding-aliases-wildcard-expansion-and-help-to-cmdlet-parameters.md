---
title: 將別名、萬用字元擴充和說明新增至 Cmdlet 參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 244c50c73972c2760e0029c7fa4f4b5764b066da
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774961"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="4498b-102">新增別名、萬用字元擴充與說明到 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="4498b-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="4498b-103">本節說明如何將別名、萬用字元擴充和說明訊息新增至 (的 Stop-Proc Cmdlet 的參數，如[建立修改系統](./creating-a-cmdlet-that-modifies-the-system.md)) 的 Cmdlet 中所述。</span><span class="sxs-lookup"><span data-stu-id="4498b-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="4498b-104">這個停止處理指示程式會嘗試使用 ([建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)) 中所述的 Get-proc Cmdlet 來停止進程。</span><span class="sxs-lookup"><span data-stu-id="4498b-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="4498b-105">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4498b-105">Defining the Cmdlet</span></span>

<span data-ttu-id="4498b-106">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="4498b-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="4498b-107">因為您要撰寫 Cmdlet 來變更系統，所以應該據以命名。</span><span class="sxs-lookup"><span data-stu-id="4498b-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="4498b-108">因為此 Cmdlet 會停止系統進程，所以會使用動詞 "Stop" （由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別所定義），並使用名詞 "Proc" 來表示進程。</span><span class="sxs-lookup"><span data-stu-id="4498b-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="4498b-109">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="4498b-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="4498b-110">下列程式碼是這個停止進程 Cmdlet 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="4498b-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="4498b-111">定義系統修改的參數</span><span class="sxs-lookup"><span data-stu-id="4498b-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="4498b-112">您的 Cmdlet 必須定義支援系統修改和使用者意見反應的參數。</span><span class="sxs-lookup"><span data-stu-id="4498b-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="4498b-113">Cmdlet 應該定義一個 `Name` 或對等的參數，讓 Cmdlet 能夠以某種識別碼來修改系統。</span><span class="sxs-lookup"><span data-stu-id="4498b-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="4498b-114">此外，此 Cmdlet 應該會定義 `Force` 和 `PassThru` 參數。</span><span class="sxs-lookup"><span data-stu-id="4498b-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="4498b-115">如需這些參數的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="4498b-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="4498b-116">定義參數別名</span><span class="sxs-lookup"><span data-stu-id="4498b-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="4498b-117">參數別名可以是替代名稱或定義完善的1個字母或兩個字母的簡短名稱，以用於 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="4498b-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="4498b-118">在這兩種情況下，使用別名的目標是要從命令列簡化使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="4498b-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="4498b-119">Windows PowerShell 支援透過[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性使用宣告語法 [Alias ( # A1] 的參數別名。</span><span class="sxs-lookup"><span data-stu-id="4498b-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="4498b-120">下列程式碼顯示如何將別名加入至 `Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="4498b-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="4498b-121">除了使用[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性以外，Windows PowerShell 執行時間也會執行部分名稱比對，即使未指定別名也一樣。</span><span class="sxs-lookup"><span data-stu-id="4498b-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="4498b-122">例如，如果您的 Cmdlet 具有 `FileName` 參數，而且是以開頭的唯一參數 `F` ，則使用者可以輸入、、 `Filename` 、 `Filenam` 或 `File` ， `Fi` 而且仍然會將 `F` 專案辨識為 `FileName` 參數。</span><span class="sxs-lookup"><span data-stu-id="4498b-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="4498b-123">建立參數的說明</span><span class="sxs-lookup"><span data-stu-id="4498b-123">Creating Help for Parameters</span></span>

<span data-ttu-id="4498b-124">Windows PowerShell 可讓您建立 Cmdlet 參數的說明。</span><span class="sxs-lookup"><span data-stu-id="4498b-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="4498b-125">請針對用於系統修改和使用者意見反應的任何參數執行此動作。</span><span class="sxs-lookup"><span data-stu-id="4498b-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="4498b-126">若要讓每個參數都支援說明，您可以 `HelpMessage` 在[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告中設定 attribute 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4498b-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="4498b-127">此關鍵字會定義要向使用者顯示的文字，以取得使用參數的協助。</span><span class="sxs-lookup"><span data-stu-id="4498b-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="4498b-128">您也可以設定 `HelpMessageBaseName` 關鍵字來識別要用於訊息之資源的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="4498b-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="4498b-129">如果您設定此關鍵字，則也必須設定 `HelpMessageResourceId` 關鍵字來指定資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="4498b-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="4498b-130">這個 Stop-Proc Cmdlet 的下列程式碼會定義 `HelpMessage` 參數的 attribute 關鍵字 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="4498b-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="4498b-131">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="4498b-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="4498b-132">您的 Cmdlet 必須覆寫輸入處理方法，這通常會是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="4498b-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="4498b-133">修改系統時，此 Cmdlet 應呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以允許使用者在進行變更之前提供意見反應。（& i）..。</span><span class="sxs-lookup"><span data-stu-id="4498b-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="4498b-134">如需這些方法的詳細資訊，請參閱[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="4498b-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="4498b-135">支援萬用字元展開</span><span class="sxs-lookup"><span data-stu-id="4498b-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="4498b-136">若要允許選取多個物件，您的 Cmdlet 可以使用[Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)和[Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)類別，為參數輸入提供萬用字元擴充支援。</span><span class="sxs-lookup"><span data-stu-id="4498b-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="4498b-137">萬用字元模式的範例包括 lsa \*、 \* .txt 和 [a-c] \* 。</span><span class="sxs-lookup"><span data-stu-id="4498b-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="4498b-138">當模式包含應逐字使用的字元時，請使用後引號字元 (') 做為換用字元。</span><span class="sxs-lookup"><span data-stu-id="4498b-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="4498b-139">檔案和路徑名稱的萬用字元擴充是常見案例的範例，當需要選取多個物件時，此 Cmdlet 可能會想要允許路徑輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="4498b-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="4498b-140">常見的情況是在檔案系統中，使用者想要查看位於目前資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="4498b-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="4498b-141">您應該只需要很少的自訂萬用字元模式比對。</span><span class="sxs-lookup"><span data-stu-id="4498b-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="4498b-142">在此情況下，您的 Cmdlet 應支援萬用字元擴充的完整 POSIX 1003.2、3.13 規格，或下列簡化的子集：</span><span class="sxs-lookup"><span data-stu-id="4498b-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="4498b-143">**問號 (？ ) 。**</span><span class="sxs-lookup"><span data-stu-id="4498b-143">**Question mark (?).**</span></span> <span data-ttu-id="4498b-144">符合指定位置的任何字元。</span><span class="sxs-lookup"><span data-stu-id="4498b-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="4498b-145">**星號 (\*) 。**</span><span class="sxs-lookup"><span data-stu-id="4498b-145">**Asterisk (\*).**</span></span> <span data-ttu-id="4498b-146">符合從指定位置開始的零個或多個字元。</span><span class="sxs-lookup"><span data-stu-id="4498b-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="4498b-147">**左括弧 ( [) 。**</span><span class="sxs-lookup"><span data-stu-id="4498b-147">**Open bracket ([).**</span></span> <span data-ttu-id="4498b-148">引進的模式括號運算式可以包含字元或字元範圍。</span><span class="sxs-lookup"><span data-stu-id="4498b-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="4498b-149">如果需要範圍，則會使用連字號 ( ) 來表示範圍。</span><span class="sxs-lookup"><span data-stu-id="4498b-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="4498b-150">**右括弧 (] ) 。**</span><span class="sxs-lookup"><span data-stu-id="4498b-150">**Close bracket (]).**</span></span> <span data-ttu-id="4498b-151">結束模式括號運算式。</span><span class="sxs-lookup"><span data-stu-id="4498b-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="4498b-152">**後引號 escape 字元 (') 。**</span><span class="sxs-lookup"><span data-stu-id="4498b-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="4498b-153">表示應該逐字採用下一個字元。</span><span class="sxs-lookup"><span data-stu-id="4498b-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="4498b-154">請注意，當您從命令列指定後引號字元時 (與以程式設計方式指定) 相反，必須指定兩次後引號 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="4498b-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="4498b-155">如需萬用字元模式的詳細資訊，請參閱[在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4498b-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="4498b-156">下列程式碼示範如何設定萬用字元選項，並定義用來解析此 Cmdlet 之參數的萬用字元模式 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="4498b-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="4498b-157">下列程式碼顯示如何測試進程名稱是否符合定義的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="4498b-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="4498b-158">請注意，在此情況下，如果進程名稱與模式不符，則 Cmdlet 會繼續進行，以取得下一個進程名稱。</span><span class="sxs-lookup"><span data-stu-id="4498b-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="4498b-159">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4498b-159">Code Sample</span></span>

<span data-ttu-id="4498b-160">如需完整的 c # 範例程式碼，請參閱[StopProcessSample03 範例](./stopprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="4498b-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="4498b-161">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="4498b-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="4498b-162">Windows PowerShell 會使用 .Net 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="4498b-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="4498b-163">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="4498b-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="4498b-164">如需定義新類型或擴充現有類型的詳細資訊，請參閱[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="4498b-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="4498b-165">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4498b-165">Building the Cmdlet</span></span>

<span data-ttu-id="4498b-166">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="4498b-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4498b-167">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="4498b-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4498b-168">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4498b-168">Testing the Cmdlet</span></span>

<span data-ttu-id="4498b-169">當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="4498b-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="4498b-170">讓我們來測試範例的 Stop-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4498b-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="4498b-171">如需從命令列使用 Cmdlet 的詳細資訊，請參閱[使用 Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="4498b-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="4498b-172">啟動 Windows PowerShell，並使用停止程式來停止使用參數之 ProcessName 別名的進程 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="4498b-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    <span data-ttu-id="4498b-173">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4498b-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="4498b-174">在命令列上進行下列專案。</span><span class="sxs-lookup"><span data-stu-id="4498b-174">Make the following entry on the command line.</span></span> <span data-ttu-id="4498b-175">因為 Name 參數是必要的，所以系統會提示您輸入。</span><span class="sxs-lookup"><span data-stu-id="4498b-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="4498b-176">輸入 "！？"</span><span class="sxs-lookup"><span data-stu-id="4498b-176">Entering "!?"</span></span> <span data-ttu-id="4498b-177">顯示與參數相關聯的解說文字。</span><span class="sxs-lookup"><span data-stu-id="4498b-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="4498b-178">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4498b-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="4498b-179">現在，請進行下列專案，以停止符合萬用字元模式 "\* note" 的所有處理常式 \* 。</span><span class="sxs-lookup"><span data-stu-id="4498b-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="4498b-180">在您停止每個符合模式的處理常式之前，系統會先提示您。</span><span class="sxs-lookup"><span data-stu-id="4498b-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

    <span data-ttu-id="4498b-181">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4498b-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    <span data-ttu-id="4498b-182">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4498b-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    <span data-ttu-id="4498b-183">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="4498b-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="4498b-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4498b-184">See Also</span></span>

[<span data-ttu-id="4498b-185">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4498b-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="4498b-186">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4498b-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="4498b-187">[擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4498b-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="4498b-188">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4498b-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="4498b-189">在 Cmdlet 參數中支援萬用字元</span><span class="sxs-lookup"><span data-stu-id="4498b-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="4498b-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4498b-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
