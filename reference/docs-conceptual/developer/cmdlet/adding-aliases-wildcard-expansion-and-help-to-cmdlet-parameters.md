---
ms.date: 09/13/2016
ms.topic: reference
title: 新增別名、萬用字元擴充與說明到 Cmdlet 參數
description: 新增別名、萬用字元擴充與說明到 Cmdlet 參數
ms.openlocfilehash: f0f07796370b4613b1ca0ad17b16c6598bfa438d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660636"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="b33ad-103">新增別名、萬用字元擴充與說明到 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="b33ad-103">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="b33ad-104">本節說明如何將別名、萬用字元擴充和說明訊息新增至 Stop-Proc Cmdlet 的參數中， (在 [建立可修改系統](./creating-a-cmdlet-that-modifies-the-system.md)) 的 Cmdlet 中所述。</span><span class="sxs-lookup"><span data-stu-id="b33ad-104">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="b33ad-105">此 Stop-Proc 指令程式會嘗試停止使用 Get-Proc Cmdlet 抓取的處理常式， () [建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="b33ad-105">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="b33ad-106">定義 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b33ad-106">Defining the Cmdlet</span></span>

<span data-ttu-id="b33ad-107">Cmdlet 建立的第一個步驟，一律會命名 Cmdlet 並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="b33ad-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b33ad-108">因為您要撰寫 Cmdlet 來變更系統，所以應該據此命名。</span><span class="sxs-lookup"><span data-stu-id="b33ad-108">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="b33ad-109">由於此 Cmdlet 會停止系統進程，因此它會使用 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 類別所定義的動詞 "Stop"，並以名詞 "Proc" 表示進程。</span><span class="sxs-lookup"><span data-stu-id="b33ad-109">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="b33ad-110">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞命令名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-110">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b33ad-111">下列程式碼是此 Stop-Proc Cmdlet 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="b33ad-111">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="b33ad-112">定義修改系統的參數</span><span class="sxs-lookup"><span data-stu-id="b33ad-112">Defining Parameters for System Modification</span></span>

<span data-ttu-id="b33ad-113">您的 Cmdlet 必須定義支援系統修改和使用者意見反應的參數。</span><span class="sxs-lookup"><span data-stu-id="b33ad-113">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="b33ad-114">Cmdlet 應定義 `Name` 參數或對等專案，讓 Cmdlet 能夠以某種識別碼來修改系統。</span><span class="sxs-lookup"><span data-stu-id="b33ad-114">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="b33ad-115">此外，此 Cmdlet 也應定義 `Force` 和 `PassThru` 參數。</span><span class="sxs-lookup"><span data-stu-id="b33ad-115">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="b33ad-116">如需這些參數的詳細資訊，請參閱 [建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-116">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="b33ad-117">定義參數別名</span><span class="sxs-lookup"><span data-stu-id="b33ad-117">Defining a Parameter Alias</span></span>

<span data-ttu-id="b33ad-118">參數別名可以是 Cmdlet 參數的替代名稱或定義完善的1個字母或2個字母的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="b33ad-118">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="b33ad-119">在這兩種情況下，使用別名的目標是要從命令列簡化使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="b33ad-119">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="b33ad-120">Windows PowerShell 透過 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 屬性支援參數別名，其使用宣告語法 [Alias ( # A1]。</span><span class="sxs-lookup"><span data-stu-id="b33ad-120">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="b33ad-121">下列程式碼顯示如何將別名加入至 `Name` 參數。</span><span class="sxs-lookup"><span data-stu-id="b33ad-121">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="b33ad-122">除了使用 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 屬性以外，Windows PowerShell 執行時間也會執行部分名稱比對，即使未指定別名也一樣。</span><span class="sxs-lookup"><span data-stu-id="b33ad-122">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="b33ad-123">例如，如果您的 Cmdlet 有一個 `FileName` 參數，而且這是以開頭的唯一參數 `F` ，則使用者可以輸入 `Filename` 、、、 `Filenam` 或， `File` `Fi` `F` 並且仍將專案辨識為 `FileName` 參數。</span><span class="sxs-lookup"><span data-stu-id="b33ad-123">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="b33ad-124">建立參數的說明</span><span class="sxs-lookup"><span data-stu-id="b33ad-124">Creating Help for Parameters</span></span>

<span data-ttu-id="b33ad-125">Windows PowerShell 可讓您建立 Cmdlet 參數的說明。</span><span class="sxs-lookup"><span data-stu-id="b33ad-125">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="b33ad-126">針對用於系統修改和使用者意見反應的任何參數，請這麼做。</span><span class="sxs-lookup"><span data-stu-id="b33ad-126">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="b33ad-127">針對每個支援協助的參數，您可以 `HelpMessage` 在 [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 屬性宣告中設定 attribute 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b33ad-127">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="b33ad-128">此關鍵字會定義要顯示給使用者的文字，以取得使用參數的協助。</span><span class="sxs-lookup"><span data-stu-id="b33ad-128">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="b33ad-129">您也可以設定 `HelpMessageBaseName` 關鍵字，以識別要用於訊息的資源基底名稱。</span><span class="sxs-lookup"><span data-stu-id="b33ad-129">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="b33ad-130">如果設定此關鍵字，您也必須設定 `HelpMessageResourceId` 關鍵字來指定資源識別碼。</span><span class="sxs-lookup"><span data-stu-id="b33ad-130">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="b33ad-131">此 Stop-Proc Cmdlet 中的下列程式碼會定義 `HelpMessage` 參數的 attribute 關鍵字 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="b33ad-131">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b33ad-132">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="b33ad-132">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b33ad-133">您的 Cmdlet 必須覆寫輸入處理方法，最常見的方法是 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-133">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="b33ad-134">修改系統時，此 Cmdlet 應該呼叫 ShouldProcess 和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以允許使用者在進行變更之前提供意見反應。」」（system [.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ）。</span><span class="sxs-lookup"><span data-stu-id="b33ad-134">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="b33ad-135">如需這些方法的詳細資訊，請參閱 [建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-135">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="b33ad-136">支援萬用字元展開</span><span class="sxs-lookup"><span data-stu-id="b33ad-136">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="b33ad-137">若要允許選取多個物件，您的 Cmdlet 可以使用 [Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 和 [Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) 類別來提供參數輸入的萬用字元擴充支援。</span><span class="sxs-lookup"><span data-stu-id="b33ad-137">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="b33ad-138">萬用字元模式的範例有 lsa \*、 \* .txt 和 [a-c] \* 。</span><span class="sxs-lookup"><span data-stu-id="b33ad-138">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="b33ad-139">當模式包含應逐字使用的字元時，請使用後引號字元 (') 作為 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="b33ad-139">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="b33ad-140">檔案和路徑名稱的萬用字元擴充是常見案例的範例，在需要選取多個物件時，此 Cmdlet 可能會想要允許路徑輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="b33ad-140">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="b33ad-141">常見的案例是在檔案系統中，使用者想要查看目前資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="b33ad-141">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="b33ad-142">您只需要很少的自訂萬用字元模式比對。</span><span class="sxs-lookup"><span data-stu-id="b33ad-142">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="b33ad-143">在此情況下，您的 Cmdlet 應該支援萬用字元擴充的完整 POSIX 1003.2、3.13 規格或下列簡化子集：</span><span class="sxs-lookup"><span data-stu-id="b33ad-143">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="b33ad-144">**問號 (？ ) 。**</span><span class="sxs-lookup"><span data-stu-id="b33ad-144">**Question mark (?).**</span></span> <span data-ttu-id="b33ad-145">符合指定位置的任何字元。</span><span class="sxs-lookup"><span data-stu-id="b33ad-145">Matches any character at the specified location.</span></span>

- <span data-ttu-id="b33ad-146">**星號 (\*) 。**</span><span class="sxs-lookup"><span data-stu-id="b33ad-146">**Asterisk (\*).**</span></span> <span data-ttu-id="b33ad-147">符合從指定位置開始的零或多個字元。</span><span class="sxs-lookup"><span data-stu-id="b33ad-147">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="b33ad-148">**左括弧 ( [) ]。**</span><span class="sxs-lookup"><span data-stu-id="b33ad-148">**Open bracket ([).**</span></span> <span data-ttu-id="b33ad-149">引進可包含字元或字元範圍的模式括號運算式。</span><span class="sxs-lookup"><span data-stu-id="b33ad-149">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="b33ad-150">如果需要範圍，則會使用連字號 (-) 來指出範圍。</span><span class="sxs-lookup"><span data-stu-id="b33ad-150">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="b33ad-151">**右括弧 (] ) 。**</span><span class="sxs-lookup"><span data-stu-id="b33ad-151">**Close bracket (]).**</span></span> <span data-ttu-id="b33ad-152">結束模式括號運算式。</span><span class="sxs-lookup"><span data-stu-id="b33ad-152">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="b33ad-153">**反向引號 escape 字元 (') 。**</span><span class="sxs-lookup"><span data-stu-id="b33ad-153">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="b33ad-154">表示應以文字形式取得下一個字元。</span><span class="sxs-lookup"><span data-stu-id="b33ad-154">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="b33ad-155">請注意，從命令列指定後引號字元 (與以程式設計的方式指定時，不是以程式設計的方式) ，就必須指定後引號 escape 字元兩次。</span><span class="sxs-lookup"><span data-stu-id="b33ad-155">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="b33ad-156">如需萬用字元模式的詳細資訊，請參閱 [在 Cmdlet 參數中支援萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-156">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="b33ad-157">下列程式碼示範如何設定萬用字元選項，並定義用來解析此 Cmdlet 之參數的萬用字元模式 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="b33ad-157">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="b33ad-158">下列程式碼示範如何測試進程名稱是否符合已定義的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="b33ad-158">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="b33ad-159">請注意，在此情況下，如果處理常式名稱不符合模式，Cmdlet 會繼續進行，以取得下一個進程名稱。</span><span class="sxs-lookup"><span data-stu-id="b33ad-159">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="b33ad-160">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b33ad-160">Code Sample</span></span>

<span data-ttu-id="b33ad-161">如需完整的 c # 範例程式碼，請參閱 [StopProcessSample03 範例](./stopprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-161">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="b33ad-162">定義物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="b33ad-162">Define Object Types and Formatting</span></span>

<span data-ttu-id="b33ad-163">Windows PowerShell 使用 .Net 物件在 Cmdlet 之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="b33ad-163">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="b33ad-164">因此，Cmdlet 可能需要定義自己的類型，或 Cmdlet 可能需要擴充另一個 Cmdlet 所提供的現有類型。</span><span class="sxs-lookup"><span data-stu-id="b33ad-164">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b33ad-165">如需定義新型別或擴充現有類型的詳細資訊，請參閱 [擴充物件類型和格式](/previous-versions//ms714665(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="b33ad-165">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b33ad-166">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b33ad-166">Building the Cmdlet</span></span>

<span data-ttu-id="b33ad-167">在執行 Cmdlet 之後，必須透過 Windows PowerShell 嵌入式管理單元向 Windows PowerShell 註冊。</span><span class="sxs-lookup"><span data-stu-id="b33ad-167">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b33ad-168">如需註冊 Cmdlet 的詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="b33ad-168">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b33ad-169">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b33ad-169">Testing the Cmdlet</span></span>

<span data-ttu-id="b33ad-170">當您的 Cmdlet 註冊 Windows PowerShell 時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="b33ad-170">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="b33ad-171">讓我們測試範例 Stop-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b33ad-171">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="b33ad-172">如需從命令列使用 Cmdlet 的詳細資訊，請參閱 [Windows PowerShell 的消費者入門](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="b33ad-172">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="b33ad-173">啟動 Windows PowerShell，並使用 Stop-Proc 來停止使用參數 ProcessName 別名的進程 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="b33ad-173">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    <span data-ttu-id="b33ad-174">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b33ad-174">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="b33ad-175">在命令列上進行下列專案。</span><span class="sxs-lookup"><span data-stu-id="b33ad-175">Make the following entry on the command line.</span></span> <span data-ttu-id="b33ad-176">因為 Name 參數是必要的，所以系統會提示您輸入。</span><span class="sxs-lookup"><span data-stu-id="b33ad-176">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="b33ad-177">輸入 "！？"</span><span class="sxs-lookup"><span data-stu-id="b33ad-177">Entering "!?"</span></span> <span data-ttu-id="b33ad-178">顯示與參數相關聯的解說文字。</span><span class="sxs-lookup"><span data-stu-id="b33ad-178">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="b33ad-179">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b33ad-179">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="b33ad-180">現在，請輸入下列專案，以停止所有符合萬用字元模式 "\* note" 的處理常式 \* 。</span><span class="sxs-lookup"><span data-stu-id="b33ad-180">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="b33ad-181">在停止符合模式的每個處理常式之前，系統會提示您。</span><span class="sxs-lookup"><span data-stu-id="b33ad-181">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

    <span data-ttu-id="b33ad-182">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b33ad-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    <span data-ttu-id="b33ad-183">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b33ad-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    <span data-ttu-id="b33ad-184">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="b33ad-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="b33ad-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b33ad-185">See Also</span></span>

[<span data-ttu-id="b33ad-186">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b33ad-186">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b33ad-187">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b33ad-187">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="b33ad-188">[擴充物件類型和格式化](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b33ad-188">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="b33ad-189">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b33ad-189">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b33ad-190">在 Cmdlet 參數中支援萬用字元</span><span class="sxs-lookup"><span data-stu-id="b33ad-190">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="b33ad-191">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b33ad-191">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
