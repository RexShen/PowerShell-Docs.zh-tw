---
title: 新增萬用字元展開的別名和 Cmdlet 參數的協助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075251"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="699c6-102">新增別名、萬用字元擴充與說明到 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="699c6-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="699c6-103">本節說明如何新增萬用字元展開的別名，並說明郵件停止程序 cmdlet 的參數 (中所述[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md))。</span><span class="sxs-lookup"><span data-stu-id="699c6-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="699c6-104">此停止程序 cmdlet 會嘗試停止處理程序會擷取使用 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="699c6-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="699c6-105">在本節中的主題包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="699c6-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="699c6-106">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="699c6-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="699c6-107">修改系統定義的參數</span><span class="sxs-lookup"><span data-stu-id="699c6-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="699c6-108">定義參數別名</span><span class="sxs-lookup"><span data-stu-id="699c6-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="699c6-109">建立參數的說明</span><span class="sxs-lookup"><span data-stu-id="699c6-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="699c6-110">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="699c6-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="699c6-111">支援的萬用字元展開</span><span class="sxs-lookup"><span data-stu-id="699c6-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="699c6-112">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="699c6-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="699c6-113">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="699c6-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="699c6-114">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="699c6-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="699c6-115">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="699c6-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="699c6-116">定義此指令程式</span><span class="sxs-lookup"><span data-stu-id="699c6-116">Defining the Cmdlet</span></span>

<span data-ttu-id="699c6-117">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="699c6-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="699c6-118">因為您正在撰寫的 cmdlet，來變更系統，它應該命名。</span><span class="sxs-lookup"><span data-stu-id="699c6-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="699c6-119">由於此 cmdlet 會停止系統處理序，它會使用所定義的 「 停止 」，動詞[System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)類別，和名詞"Proc"來指出程序。</span><span class="sxs-lookup"><span data-stu-id="699c6-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="699c6-120">如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="699c6-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="699c6-121">下列程式碼會為此停止程序 cmdlet 類別定義。</span><span class="sxs-lookup"><span data-stu-id="699c6-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="699c6-122">修改系統定義的參數</span><span class="sxs-lookup"><span data-stu-id="699c6-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="699c6-123">您的指令程式必須定義參數，該修改支援系統和使用者意見反應。</span><span class="sxs-lookup"><span data-stu-id="699c6-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="699c6-124">此 cmdlet 應該定義`Name`參數或同等權限，讓此指令程式將能夠某種形式的識別項來修改系統。</span><span class="sxs-lookup"><span data-stu-id="699c6-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="699c6-125">此外，此 cmdlet 應該定義`Force`和`PassThru`參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="699c6-126">如需有關這些參數的詳細資訊，請參閱 <<c0> [ 建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="699c6-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="699c6-127">定義參數別名</span><span class="sxs-lookup"><span data-stu-id="699c6-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="699c6-128">參數別名可以是替代的名稱或針對 cmdlet 參數定義完善字母 1 或 2 個字母簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="699c6-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="699c6-129">在這兩種情況下，使用別名的目標是簡化從命令列的使用者項目。</span><span class="sxs-lookup"><span data-stu-id="699c6-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="699c6-130">Windows PowerShell 支援透過參數別名[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性，它會使用宣告語法 [Alias()]。</span><span class="sxs-lookup"><span data-stu-id="699c6-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="699c6-131">下列程式碼會示範如何將別名加入至`Name`參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="699c6-132">除了使用[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性，Windows PowerShell 執行階段執行的部分名稱比對，即使已指定任何別名。</span><span class="sxs-lookup"><span data-stu-id="699c6-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="699c6-133">例如，如果您的 cmdlet 已`FileName`參數，也就是開頭的唯一參數`F`，使用者可以輸入`Filename`， `Filenam`， `File`， `Fi`，或`F`，仍會辨識項目標示為`FileName`參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="699c6-134">建立參數的說明</span><span class="sxs-lookup"><span data-stu-id="699c6-134">Creating Help for Parameters</span></span>

<span data-ttu-id="699c6-135">Windows PowerShell 可讓您建立的 cmdlet 參數的說明。</span><span class="sxs-lookup"><span data-stu-id="699c6-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="699c6-136">用於系統修改和使用者意見反應的任何參數執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="699c6-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="699c6-137">對於支援說明每個參數，您可以設定`HelpMessage`屬性中的關鍵字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="699c6-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="699c6-138">這個關鍵字會定義要有關使用參數使用者顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="699c6-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="699c6-139">您也可以設定`HelpMessageBaseName`關鍵字來識別資源以用於訊息的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="699c6-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="699c6-140">如果您設定此關鍵字，您也必須設定`HelpMessageResourceId`關鍵字來指定資源識別項。</span><span class="sxs-lookup"><span data-stu-id="699c6-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="699c6-141">下列程式碼，從這個停止程序 cmdlet 定義`HelpMessage`屬性的關鍵字`Name`參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="699c6-142">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="699c6-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="699c6-143">您的 cmdlet 必須覆寫輸入處理方法，這是最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。</span><span class="sxs-lookup"><span data-stu-id="699c6-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="699c6-144">此 cmdlet 時修改系統，應該呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，可讓使用者若要進行變更之前，請提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="699c6-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="699c6-145">如需這些方法的詳細資訊，請參閱[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)。</span><span class="sxs-lookup"><span data-stu-id="699c6-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="699c6-146">支援的萬用字元展開</span><span class="sxs-lookup"><span data-stu-id="699c6-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="699c6-147">若要允許選取多個物件，可以使用您的 cmdlet [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)並[System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)類別提供萬用字元展開支援輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="699c6-148">萬用字元模式的範例包括 lsa \* \*.txt 和 [a-c]\*。</span><span class="sxs-lookup"><span data-stu-id="699c6-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="699c6-149">模式所包含的字元應該解譯為常值使用時，則您可以做為逸出字元後引號字元 （'）。</span><span class="sxs-lookup"><span data-stu-id="699c6-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="699c6-150">萬用字元展開的檔案和路徑的名稱是此 cmdlet 可能要允許的路徑輸入支援，需要選取多個物件時的常見案例的範例。</span><span class="sxs-lookup"><span data-stu-id="699c6-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="699c6-151">常見的案例是在檔案系統中，使用者想要查看位於目前的資料夾中的所有檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="699c6-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="699c6-152">您應該很少需要自訂的萬用字元模式比對實作。</span><span class="sxs-lookup"><span data-stu-id="699c6-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="699c6-153">在此情況下，您的指令程式應該支援完整的 POSIX 1003.2、 3.13 萬用字元展開規格或以下的簡化的子集：</span><span class="sxs-lookup"><span data-stu-id="699c6-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="699c6-154">**問號 （？）。**</span><span class="sxs-lookup"><span data-stu-id="699c6-154">**Question mark (?).**</span></span> <span data-ttu-id="699c6-155">比對任何字元，在指定的位置。</span><span class="sxs-lookup"><span data-stu-id="699c6-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="699c6-156">**星號 (\*)。**</span><span class="sxs-lookup"><span data-stu-id="699c6-156">**Asterisk (\*).**</span></span> <span data-ttu-id="699c6-157">比對零或多個字元的指定位置開始。</span><span class="sxs-lookup"><span data-stu-id="699c6-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="699c6-158">**左括號 ([])。**</span><span class="sxs-lookup"><span data-stu-id="699c6-158">**Open bracket ([).**</span></span> <span data-ttu-id="699c6-159">引進模式括號運算式可以包含字元範圍。</span><span class="sxs-lookup"><span data-stu-id="699c6-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="699c6-160">如果範圍為必要項目，是連字號 （-） 用來表示範圍。</span><span class="sxs-lookup"><span data-stu-id="699c6-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="699c6-161">**右括號 (])。**</span><span class="sxs-lookup"><span data-stu-id="699c6-161">**Close bracket (]).**</span></span> <span data-ttu-id="699c6-162">結束模式括號運算式。</span><span class="sxs-lookup"><span data-stu-id="699c6-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="699c6-163">**後引號逸出字元 （'）。**</span><span class="sxs-lookup"><span data-stu-id="699c6-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="699c6-164">表示下一個字元應該解譯為常值帶。</span><span class="sxs-lookup"><span data-stu-id="699c6-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="699c6-165">請注意，當指定時從命令列 （而不是以程式設計方式指定） 的後引號字元後, 引號逸出字元必須指定兩次。</span><span class="sxs-lookup"><span data-stu-id="699c6-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="699c6-166">如需萬用字元模式的詳細資訊，請參閱[在 Cmdlet 參數中的 支援使用萬用字元](./supporting-wildcard-characters-in-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="699c6-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="699c6-167">下列程式碼示範如何設定萬用字元選項，並定義用來解析萬用字元模式`Name`此 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="699c6-168">下列程式碼會示範如何測試處理序名稱是否符合已定義的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="699c6-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="699c6-169">請注意，在此情況下，是否處理序名稱與模式不符，此 cmdlet 會繼續上取得下一個程序名稱。</span><span class="sxs-lookup"><span data-stu-id="699c6-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="699c6-170">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="699c6-170">Code Sample</span></span>

<span data-ttu-id="699c6-171">完整C#程式碼範例，請參閱 < [StopProcessSample03 範例](./stopprocesssample03-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="699c6-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="699c6-172">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="699c6-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="699c6-173">Windows PowerShell cmdlet 使用.Net 物件之間傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="699c6-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="699c6-174">因此，cmdlet 可能需要定義自己的類型，或可能需要擴充現有的類型提供的另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="699c6-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="699c6-175">如需定義新的型別或擴充現有類型的詳細資訊，請參閱[延伸的物件類型與格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。</span><span class="sxs-lookup"><span data-stu-id="699c6-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="699c6-176">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="699c6-176">Building the Cmdlet</span></span>

<span data-ttu-id="699c6-177">在實作之後的 cmdlet，它必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="699c6-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="699c6-178">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="699c6-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="699c6-179">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="699c6-179">Testing the Cmdlet</span></span>

<span data-ttu-id="699c6-180">當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="699c6-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="699c6-181">我們來測試範例停止程序 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="699c6-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="699c6-182">如需使用 cmdlet，從命令列的詳細資訊，請參閱[Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="699c6-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="699c6-183">啟動 Windows PowerShell 並使用停止程序，停止處理序使用的 ProcessName 別名`Name`參數。</span><span class="sxs-lookup"><span data-stu-id="699c6-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="699c6-184">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="699c6-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="699c6-185">請在命令列上的下列項目。</span><span class="sxs-lookup"><span data-stu-id="699c6-185">Make the following entry on the command line.</span></span> <span data-ttu-id="699c6-186">Name 參數是必要的因為它會提示您。</span><span class="sxs-lookup"><span data-stu-id="699c6-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="699c6-187">輸入 「 ！？"</span><span class="sxs-lookup"><span data-stu-id="699c6-187">Entering "!?"</span></span> <span data-ttu-id="699c6-188">會顯示與參數關聯的說明文字。</span><span class="sxs-lookup"><span data-stu-id="699c6-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="699c6-189">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="699c6-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="699c6-190">現在請停止所有符合萬用字元模式的處理序的下列項目 」 \* 注意\*"。</span><span class="sxs-lookup"><span data-stu-id="699c6-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="699c6-191">系統會提示您停止每個符合模式的處理序之前。</span><span class="sxs-lookup"><span data-stu-id="699c6-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="699c6-192">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="699c6-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="699c6-193">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="699c6-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="699c6-194">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="699c6-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="699c6-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="699c6-195">See Also</span></span>

[<span data-ttu-id="699c6-196">建立修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="699c6-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="699c6-197">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="699c6-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="699c6-198">擴充物件類型和格式</span><span class="sxs-lookup"><span data-stu-id="699c6-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="699c6-199">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="699c6-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="699c6-200">在 Cmdlet 參數支援萬用字元</span><span class="sxs-lookup"><span data-stu-id="699c6-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="699c6-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="699c6-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
