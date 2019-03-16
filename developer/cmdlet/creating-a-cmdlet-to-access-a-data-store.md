---
title: 建立可存取資料存放區的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 28d55874960f9a64b986204411d38319ef1d0da7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059519"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="33f4d-102">建立 Cmdlet 以存取資料存放區</span><span class="sxs-lookup"><span data-stu-id="33f4d-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="33f4d-103">本節說明如何建立指令程式來存取儲存的資料，透過 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="33f4d-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="33f4d-104">這種類型的指令程式會使用 Windows PowerShell 執行階段的 Windows PowerShell 提供者基礎結構，因此，在 cmdlet 類別必須衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基底類別。</span><span class="sxs-lookup"><span data-stu-id="33f4d-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="33f4d-105">此處所述選取 Str cmdlet 可以找出並選取檔案或物件中的字串。</span><span class="sxs-lookup"><span data-stu-id="33f4d-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="33f4d-106">用來識別字串的模式可以透過明確指定`Path`參數的 cmdlet 或隱含地透過`Script`參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="33f4d-107">此指令程式可使用衍生自任何 Windows PowerShell 提供者[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="33f4d-108">例如，FileSystem 提供者或變數提供者所提供的 Windows PowerShell，可以指定此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="33f4d-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="33f4d-109">如需詳細資訊 aboutWindows PowerShell 提供者，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](../prog-guide/designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

<span data-ttu-id="33f4d-110">在本節中的主題包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="33f4d-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="33f4d-111">定義在 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="33f4d-111">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="33f4d-112">定義參數的資料存取</span><span class="sxs-lookup"><span data-stu-id="33f4d-112">Defining Parameters for Data Access</span></span>](#Declaring-the-Path-Parameter)

- [<span data-ttu-id="33f4d-113">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="33f4d-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="33f4d-114">存取內容</span><span class="sxs-lookup"><span data-stu-id="33f4d-114">Accessing Content</span></span>](#Accessing-Content)

- [<span data-ttu-id="33f4d-115">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="33f4d-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="33f4d-116">定義物件類型和格式設定</span><span class="sxs-lookup"><span data-stu-id="33f4d-116">Defining Object Types and Formatting</span></span>](#Declaring-Search-Support-Parameters)

- [<span data-ttu-id="33f4d-117">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="33f4d-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="33f4d-118">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="33f4d-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="33f4d-119">定義在 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="33f4d-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="33f4d-120">Cmdlet 建立的第一個步驟一律命名 cmdlet，並實作指令程式的.NET 類別的宣告。</span><span class="sxs-lookup"><span data-stu-id="33f4d-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="33f4d-121">這個指令程式會偵測到特定的字串，所以在這裡選擇的指令動詞名稱是 「 Select 」，所定義[System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)類別。</span><span class="sxs-lookup"><span data-stu-id="33f4d-121">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="33f4d-122">名詞 」 名稱"Str"，因為此 cmdlet 會作用在字串。</span><span class="sxs-lookup"><span data-stu-id="33f4d-122">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="33f4d-123">在下列宣告中，請注意 cmdlet 動詞和名詞名稱會反映在 cmdlet 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="33f4d-123">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="33f4d-124">如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-124">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="33f4d-125">這個指令程式的.NET 類別必須衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基底類別，因為它會提供 Windows PowerShell 執行階段公開 （expose） 的 Windows PowerShell 提供者所需的支援基礎結構。</span><span class="sxs-lookup"><span data-stu-id="33f4d-125">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="33f4d-126">請注意，此 cmdlet 也會利用.NET Framework 規則運算式類別，例如[System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-126">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="33f4d-127">下列程式碼會為此選取 Str cmdlet 類別定義。</span><span class="sxs-lookup"><span data-stu-id="33f4d-127">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="33f4d-128">此 cmdlet 定義加入設定的預設參數`DefaultParameterSetName`屬性至類別宣告的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="33f4d-128">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="33f4d-129">預設參數集`PatternParameterSet`時會使用`Script`未指定參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-129">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="33f4d-130">如需有關此參數集的詳細資訊，請參閱 <<c0> `Pattern` 和`Script`參數討論下, 一節。</span><span class="sxs-lookup"><span data-stu-id="33f4d-130">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="33f4d-131">定義參數的資料存取</span><span class="sxs-lookup"><span data-stu-id="33f4d-131">Defining Parameters for Data Access</span></span>

<span data-ttu-id="33f4d-132">此 cmdlet 會定義數個參數可讓使用者存取，並檢查儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="33f4d-132">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="33f4d-133">這些參數包含`Path`參數，指出資料存放區位置`Pattern`參數，在搜尋中，指定要使用的模式和支援搜尋的執行方式的其他幾個參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-133">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="33f4d-134">定義參數的基本概念的相關資訊，請參閱[加入參數，該程序的命令列輸入](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-134">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="33f4d-135">宣告的路徑參數</span><span class="sxs-lookup"><span data-stu-id="33f4d-135">Declaring the Path Parameter</span></span>

<span data-ttu-id="33f4d-136">若要尋找的資料存放區，這個指令程式必須使用 Windows PowerShell 路徑，來識別 Windows PowerShell 提供者是設計用來存取資料存放區。</span><span class="sxs-lookup"><span data-stu-id="33f4d-136">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="33f4d-137">因此，它會定義`Path`參數的型別字串陣列，表示提供者的位置。</span><span class="sxs-lookup"><span data-stu-id="33f4d-137">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="33f4d-138">請注意，這個參數所屬的兩個不同的參數集，而且它具有別名。</span><span class="sxs-lookup"><span data-stu-id="33f4d-138">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="33f4d-139">兩個[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性宣告`Path`參數屬於`ScriptParameterSet`而`PatternParameterSet`。</span><span class="sxs-lookup"><span data-stu-id="33f4d-139">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="33f4d-140">如需參數集的詳細資訊，請參閱[將參數集加入至指令程式](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-140">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="33f4d-141">[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性會宣告`PSPath`別名，以供`Path`參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-141">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="33f4d-142">與其他指令程式，存取 Windows PowerShell 提供者的一致性，強烈建議宣告此別名。</span><span class="sxs-lookup"><span data-stu-id="33f4d-142">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="33f4d-143">如需詳細資訊 aboutWindows PowerShell 路徑，請參閱 「 PowerShell 路徑概念 」 中[Windows PowerShell 的運作方式](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-143">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="33f4d-144">宣告的模式參數</span><span class="sxs-lookup"><span data-stu-id="33f4d-144">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="33f4d-145">若要指定要搜尋的模式，此 cmdlet 會宣告`Pattern`是字串陣列的參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-145">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="33f4d-146">資料存放區中發現任何模式時，會傳回正數的結果。</span><span class="sxs-lookup"><span data-stu-id="33f4d-146">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="33f4d-147">請注意，這些模式可以編譯成已編譯規則運算式陣列或陣列常值搜尋所使用的萬用字元模式。</span><span class="sxs-lookup"><span data-stu-id="33f4d-147">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="33f4d-148">當指定這個參數時，此 cmdlet 會使用預設參數集`PatternParameterSet`。</span><span class="sxs-lookup"><span data-stu-id="33f4d-148">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="33f4d-149">在此情況下，此 cmdlet 會使用選取字串此處指定的模式。</span><span class="sxs-lookup"><span data-stu-id="33f4d-149">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="33f4d-150">相反地，`Script`參數也可用來提供的指令碼，包含的模式。</span><span class="sxs-lookup"><span data-stu-id="33f4d-150">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="33f4d-151">`Script`和`Pattern`參數會定義兩個不同的參數集合，因此兩者互斥。</span><span class="sxs-lookup"><span data-stu-id="33f4d-151">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="33f4d-152">宣告搜尋支援參數</span><span class="sxs-lookup"><span data-stu-id="33f4d-152">Declaring Search Support Parameters</span></span>

<span data-ttu-id="33f4d-153">此 cmdlet 會定義下列可用來修改此指令程式的搜尋功能的支援參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-153">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="33f4d-154">`Script`參數指定可用來提供此 cmdlet 的替代的搜尋機制的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="33f4d-154">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="33f4d-155">指令碼必須包含用來比對的模式，並傳回[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)物件。</span><span class="sxs-lookup"><span data-stu-id="33f4d-155">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="33f4d-156">請注意，此參數也會識別的 unique 參數`ScriptParameterSet`參數集。</span><span class="sxs-lookup"><span data-stu-id="33f4d-156">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="33f4d-157">當 Windows PowerShell 執行階段便會看到此參數時，它會使用屬於的參數`ScriptParameterSet`參數集。</span><span class="sxs-lookup"><span data-stu-id="33f4d-157">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="33f4d-158">`SimpleMatch`參數是切換參數，指出此 cmdlet 是否要明確地符合的模式，所提供。</span><span class="sxs-lookup"><span data-stu-id="33f4d-158">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="33f4d-159">當使用者指定在命令列參數 (`true`)，此 cmdlet 使用的模式，所提供。</span><span class="sxs-lookup"><span data-stu-id="33f4d-159">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="33f4d-160">如果未指定參數 (`false`)，此 cmdlet 會使用規則運算式。</span><span class="sxs-lookup"><span data-stu-id="33f4d-160">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="33f4d-161">此參數的預設值是`false`。</span><span class="sxs-lookup"><span data-stu-id="33f4d-161">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="33f4d-162">`CaseSensitive`參數是切換參數，指出是否要執行區分大小寫的搜尋。</span><span class="sxs-lookup"><span data-stu-id="33f4d-162">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="33f4d-163">當使用者指定在命令列參數 (`true`)、 指令程式會檢查是否有大寫和小寫字元比較時的模式。</span><span class="sxs-lookup"><span data-stu-id="33f4d-163">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="33f4d-164">如果未指定參數 (`false`)，此 cmdlet 不區分大寫和小寫。</span><span class="sxs-lookup"><span data-stu-id="33f4d-164">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="33f4d-165">比方說 「 MyFile"和"myfile"會同時傳回為正數的點擊。</span><span class="sxs-lookup"><span data-stu-id="33f4d-165">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="33f4d-166">此參數的預設值是`false`。</span><span class="sxs-lookup"><span data-stu-id="33f4d-166">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="33f4d-167">`Exclude`和`Include`參數會識別明確排除或包含在搜尋中的項目。</span><span class="sxs-lookup"><span data-stu-id="33f4d-167">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="33f4d-168">根據預設，cmdlet 會搜尋資料存放區中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="33f4d-168">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="33f4d-169">不過，cmdlet 所執行的搜尋範圍限制，這些參數可以是用來明確指出要包含在搜尋中的項目或省略。</span><span class="sxs-lookup"><span data-stu-id="33f4d-169">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="33f4d-170">宣告參數集</span><span class="sxs-lookup"><span data-stu-id="33f4d-170">Declaring Parameter Sets</span></span>

<span data-ttu-id="33f4d-171">此 cmdlet 會使用兩個參數集 (`ScriptParameterSet`和`PatternParameterSet`，這是預設值) 當做用於資料存取的兩個參數集的名稱。</span><span class="sxs-lookup"><span data-stu-id="33f4d-171">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="33f4d-172">`PatternParameterSet` 是預設參數集，當使用`Pattern`指定參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-172">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="33f4d-173">`ScriptParameterSet` 使用者指定替代的搜尋機制時，會使用`Script`參數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-173">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="33f4d-174">如需參數集的詳細資訊，請參閱[將參數集加入至指令程式](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-174">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="33f4d-175">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="33f4d-175">Overriding Input Processing Methods</span></span>

<span data-ttu-id="33f4d-176">一或多個的輸入處理方法，必須覆寫 Cmdlet [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="33f4d-176">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="33f4d-177">如需有關輸入的處理方法的詳細資訊，請參閱 <<c0> [ 建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-177">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="33f4d-178">此 cmdlet 會覆寫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法來建立陣列的編譯的規則運算式，在啟動時。</span><span class="sxs-lookup"><span data-stu-id="33f4d-178">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="33f4d-179">這會增加在不使用簡單比對的搜尋時的效能。</span><span class="sxs-lookup"><span data-stu-id="33f4d-179">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="33f4d-180">此 cmdlet 也會覆寫[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法來處理使用者進行命令列的字串選取項目。</span><span class="sxs-lookup"><span data-stu-id="33f4d-180">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="33f4d-181">它將結果字串選取範圍的自訂物件的形式寫入藉由呼叫私用**MatchString**方法。</span><span class="sxs-lookup"><span data-stu-id="33f4d-181">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="33f4d-182">存取內容</span><span class="sxs-lookup"><span data-stu-id="33f4d-182">Accessing Content</span></span>

<span data-ttu-id="33f4d-183">您的 cmdlet 必須開啟，使其可以存取資料，Windows PowerShell 路徑所指定的提供者。</span><span class="sxs-lookup"><span data-stu-id="33f4d-183">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="33f4d-184">[System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState)物件的存取提供者使用的 runspace，而[System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider)屬性cmdlet 用來開啟提供者。</span><span class="sxs-lookup"><span data-stu-id="33f4d-184">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="33f4d-185">擷取提供內容的存取權[System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics)開啟提供者的物件。</span><span class="sxs-lookup"><span data-stu-id="33f4d-185">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="33f4d-186">此範例選取 Str cmdlet 會使用[System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content)屬性公開要掃描的內容。</span><span class="sxs-lookup"><span data-stu-id="33f4d-186">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="33f4d-187">它可以呼叫[System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader)方法，並傳遞必要的 Windows PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="33f4d-187">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="33f4d-188">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="33f4d-188">Code Sample</span></span>

<span data-ttu-id="33f4d-189">下列程式碼顯示這個版本的此選取 Str cmdlet 的實作。</span><span class="sxs-lookup"><span data-stu-id="33f4d-189">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="33f4d-190">請注意，此程式碼包含在 cmdlet 類別，由 cmdlet 所使用的私用方法的 Windows PowerShell 嵌入式管理單元程式碼用來註冊此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="33f4d-190">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="33f4d-191">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 建置 Cmdlet](#Building-the-Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-191">For more information about registering the cmdlet, see [Building the Cmdlet](#Building-the-Cmdlet).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="33f4d-192">建置此指令程式</span><span class="sxs-lookup"><span data-stu-id="33f4d-192">Building the Cmdlet</span></span>

<span data-ttu-id="33f4d-193">在實作之後的 cmdlet，您必須向 Windows PowerShell 透過 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="33f4d-193">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="33f4d-194">如需有關如何註冊 cmdlet 的詳細資訊，請參閱 <<c0> [ 如何註冊 Cmdlet、 提供者，以及裝載應用程式](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。</span><span class="sxs-lookup"><span data-stu-id="33f4d-194">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="33f4d-195">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="33f4d-195">Testing the Cmdlet</span></span>

<span data-ttu-id="33f4d-196">當您的 cmdlet 已向 Windows PowerShell 時，您可以藉由在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="33f4d-196">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="33f4d-197">下列程序可用來測試此範例選取 Str 指令程式。</span><span class="sxs-lookup"><span data-stu-id="33f4d-197">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="33f4d-198">啟動 Windows PowerShell，並搜尋資訊檔中的運算式".NET"的行項目。</span><span class="sxs-lookup"><span data-stu-id="33f4d-198">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="33f4d-199">請注意，引號括住路徑的名稱，才會組成多個字組的路徑。</span><span class="sxs-lookup"><span data-stu-id="33f4d-199">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="33f4d-200">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="33f4d-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="33f4d-201">搜尋 「 結束 」，資訊檔的字行的項目，後面接著任何其他文字。</span><span class="sxs-lookup"><span data-stu-id="33f4d-201">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="33f4d-202">`SimpleMatch`參數使用的預設值`false`。</span><span class="sxs-lookup"><span data-stu-id="33f4d-202">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="33f4d-203">搜尋不區分大小寫因為`CaseSensitive`參數設為`false`。</span><span class="sxs-lookup"><span data-stu-id="33f4d-203">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="33f4d-204">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="33f4d-204">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="33f4d-205">搜尋作為模式使用規則運算式的資訊檔案。</span><span class="sxs-lookup"><span data-stu-id="33f4d-205">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="33f4d-206">此 cmdlet 會搜尋依字母順序排列的字元和空格，括號括住。</span><span class="sxs-lookup"><span data-stu-id="33f4d-206">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="33f4d-207">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="33f4d-207">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="33f4d-208">執行區分大小寫搜尋便箋檔案中的 「 參數 」 這個字相符項目。</span><span class="sxs-lookup"><span data-stu-id="33f4d-208">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="33f4d-209">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="33f4d-209">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="33f4d-210">搜尋變數提供者會隨附 Windows PowerShell 有從 0 到 9 的數字值的變數。</span><span class="sxs-lookup"><span data-stu-id="33f4d-210">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="33f4d-211">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="33f4d-211">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="33f4d-212">您可以使用指令碼區塊來搜尋字串"Pos"SelectStrCommandSample.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="33f4d-212">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="33f4d-213">**Cmatch**函式的指令碼執行不區分大小寫的模式比對。</span><span class="sxs-lookup"><span data-stu-id="33f4d-213">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="33f4d-214">下列輸出隨即出現。</span><span class="sxs-lookup"><span data-stu-id="33f4d-214">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="33f4d-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33f4d-215">See Also</span></span>

[<span data-ttu-id="33f4d-216">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="33f4d-216">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="33f4d-217">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="33f4d-217">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="33f4d-218">建立 Cmdlet 會修改系統</span><span class="sxs-lookup"><span data-stu-id="33f4d-218">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="33f4d-219">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="33f4d-219">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

[<span data-ttu-id="33f4d-220">Windows PowerShell 的運作方式</span><span class="sxs-lookup"><span data-stu-id="33f4d-220">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="33f4d-221">如何註冊 Cmdlet、 提供者，以及裝載應用程式</span><span class="sxs-lookup"><span data-stu-id="33f4d-221">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="33f4d-222">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="33f4d-222">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
