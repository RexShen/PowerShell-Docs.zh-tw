---
title: 建立 Cmdlet 以存取資料存放區
ms.date: 09/13/2016
ms.openlocfilehash: a595805a820c355937e581f0e00fa2a9a9fc3df0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782135"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="fa8ff-102">建立 Cmdlet 以存取資料存放區</span><span class="sxs-lookup"><span data-stu-id="fa8ff-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="fa8ff-103">本節說明如何建立可透過 Windows PowerShell 提供者存取預存資料的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="fa8ff-104">這種類型的 Cmdlet 會使用 Windows PowerShell 執行時間的 Windows PowerShell 提供者基礎結構，因此，Cmdlet 類別必須衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基類。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="fa8ff-105">這裡所述的 Select-Str Cmdlet 可以在檔案或物件中找到並選取字串。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="fa8ff-106">用來識別字串的模式可以透過 `Path` Cmdlet 的參數或透過參數隱含地指定 `Script` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="fa8ff-107">此 Cmdlet 是設計用來使用任何衍生自[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="fa8ff-108">例如，此 Cmdlet 可以指定 FileSystem 提供者或 Windows PowerShell 所提供的變數提供者。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="fa8ff-109">如需 aboutWindows PowerShell 提供者的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](../prog-guide/designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="fa8ff-110">定義 Cmdlet 類別</span><span class="sxs-lookup"><span data-stu-id="fa8ff-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="fa8ff-111">Cmdlet 建立的第一個步驟一律為 Cmdlet 命名，並宣告可執行 Cmdlet 的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="fa8ff-112">此 Cmdlet 會偵測特定字串，因此此處選擇的動詞名稱是 "Select"，由[Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)類別所定義。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="fa8ff-113">使用名詞名稱 "Str"，因為 Cmdlet 會在字串上作用。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="fa8ff-114">在下面的宣告中，請注意 Cmdlet 動詞和名詞名稱會反映在 Cmdlet 類別的名稱中。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="fa8ff-115">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="fa8ff-116">此 Cmdlet 的 .NET 類別必須衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基類，因為它會提供 windows powershell 執行時間所需的支援，以公開 windows powershell 提供者基礎結構。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="fa8ff-117">請注意，這個 Cmdlet 也會使用 .NET Framework 的正則運算式類別，例如[system.text.regularexpressions.RegEx>。](/dotnet/api/System.Text.RegularExpressions.Regex)</span><span class="sxs-lookup"><span data-stu-id="fa8ff-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="fa8ff-118">下列程式碼是這個 Select-Str Cmdlet 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="fa8ff-119">此 Cmdlet 會定義預設參數集，方法是將 `DefaultParameterSetName` attribute 關鍵字加入至類別宣告。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="fa8ff-120">`PatternParameterSet`未指定參數時，會使用預設參數集 `Script` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="fa8ff-121">如需此參數集的詳細資訊，請 `Pattern` 參閱 `Script` 下一節中的和參數討論。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="fa8ff-122">定義資料存取的參數</span><span class="sxs-lookup"><span data-stu-id="fa8ff-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="fa8ff-123">此 Cmdlet 會定義數個參數，以允許使用者存取和檢查儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="fa8ff-124">這些參數包含的 `Path` 參數會指出資料存放區的位置、 `Pattern` 指定要在搜尋中使用之模式的參數，以及支援搜尋執行方式的其他數個參數。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="fa8ff-125">如需定義參數之基本概念的詳細資訊，請參閱[加入處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="fa8ff-126">宣告 Path 參數</span><span class="sxs-lookup"><span data-stu-id="fa8ff-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="fa8ff-127">若要找出資料存放區，此 Cmdlet 必須使用 Windows PowerShell 路徑來識別設計用來存取資料存放區的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="fa8ff-128">因此，它會定義 `Path` 類型字串陣列的參數，以指出提供者的位置。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

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

<span data-ttu-id="fa8ff-129">請注意，這個參數屬於兩個不同的參數集，而且它有一個別名。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="fa8ff-130">兩個[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)屬性會宣告 `Path` 參數屬於 `ScriptParameterSet` 和的 `PatternParameterSet` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="fa8ff-131">如需參數集的詳細資訊，請參閱[將參數集新增至 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="fa8ff-132">[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)屬性會宣告 `PSPath` 此參數的別名 `Path` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="fa8ff-133">強烈建議您宣告此別名，以與存取 Windows PowerShell 提供者的其他 Cmdlet 保持一致。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="fa8ff-134">如需 aboutWindows PowerShell 路徑的詳細資訊，請參閱[Windows Powershell 運作方式](/previous-versions//ms714658(v=vs.85))中的「PowerShell 路徑概念」。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="fa8ff-135">宣告模式參數</span><span class="sxs-lookup"><span data-stu-id="fa8ff-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="fa8ff-136">為了指定要搜尋的模式，這個 Cmdlet 會宣告一個 `Pattern` 參數，它是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="fa8ff-137">在資料存放區中找到任何模式時，會傳回正的結果。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="fa8ff-138">請注意，這些模式可以編譯成編譯的正則運算式陣列，或用於常值搜尋的萬用字元模式陣列。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

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

<span data-ttu-id="fa8ff-139">當指定這個參數時，此 Cmdlet 會使用預設參數集 `PatternParameterSet` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="fa8ff-140">在此情況下，此 Cmdlet 會使用此處指定的模式來選取字串。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="fa8ff-141">相反 `Script` 地，參數也可以用來提供包含模式的腳本。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="fa8ff-142">`Script`和 `Pattern` 參數會定義兩個不同的參數集，因此它們是互斥的。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="fa8ff-143">宣告搜尋支援參數</span><span class="sxs-lookup"><span data-stu-id="fa8ff-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="fa8ff-144">此 Cmdlet 會定義可用於修改 Cmdlet 搜尋功能的下列支援參數。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="fa8ff-145">`Script`參數會指定腳本區塊，可用來提供 Cmdlet 的替代搜尋機制。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="fa8ff-146">腳本必須包含用來比對和傳回[system.web](/dotnet/api/System.Management.Automation.PSObject)物件的模式。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="fa8ff-147">請注意，此參數也是識別參數集的唯一參數 `ScriptParameterSet` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="fa8ff-148">當 Windows PowerShell 執行時間看到此參數時，它只會使用屬於 `ScriptParameterSet` 參數集的參數。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

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

<span data-ttu-id="fa8ff-149">`SimpleMatch`參數是一個切換參數，可指出 Cmdlet 是否要在提供時明確符合模式。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="fa8ff-150">當使用者在命令列指定參數 (`true`) 時，此 Cmdlet 會使用所提供的模式。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="fa8ff-151">如果未指定參數 (`false`) ，此 Cmdlet 會使用正則運算式。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="fa8ff-152">這個參數的預設值是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="fa8ff-153">`CaseSensitive`參數是一個切換參數，它會指出是否執行區分大小寫的搜尋。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="fa8ff-154">當使用者在命令列指定參數時 () 時 `true` ，此 Cmdlet 會在比較模式時，檢查大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="fa8ff-155">如果未指定參數 (`false`) ，則 Cmdlet 不會區分大寫和小寫。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="fa8ff-156">例如，"Myfile.txt" 和 "myfile.txt" 都會傳回為正命中。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="fa8ff-157">這個參數的預設值是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="fa8ff-158">`Exclude`和 `Include` 參數會識別在搜尋中明確排除或包含的專案。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="fa8ff-159">根據預設，此 Cmdlet 會搜尋資料存放區中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="fa8ff-160">不過，若要限制 Cmdlet 所執行的搜尋，這些參數可以用來明確指出要包含在搜尋中的專案或省略。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

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

### <a name="declaring-parameter-sets"></a><span data-ttu-id="fa8ff-161">宣告參數集</span><span class="sxs-lookup"><span data-stu-id="fa8ff-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="fa8ff-162">此 Cmdlet 會使用兩個參數集 (`ScriptParameterSet` 和 `PatternParameterSet` ，這是預設) ，做為資料存取中使用的兩個參數集的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="fa8ff-163">`PatternParameterSet`是預設參數集，而且是在 `Pattern` 指定參數時使用。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="fa8ff-164">`ScriptParameterSet`當使用者透過參數指定替代搜尋機制時，會使用 `Script` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="fa8ff-165">如需參數集的詳細資訊，請參閱[將參數集新增至 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="fa8ff-166">覆寫輸入處理方法</span><span class="sxs-lookup"><span data-stu-id="fa8ff-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="fa8ff-167">Cmdlet 必須覆寫[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別的一或多個輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="fa8ff-168">如需輸入處理方法的詳細資訊，請參閱[建立您的第一個 Cmdlet](./creating-a-cmdlet-without-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="fa8ff-169">此 Cmdlet 會覆寫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，以在啟動時建立已編譯之正則運算式的陣列。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="fa8ff-170">這會在不使用簡單比對的搜尋期間增加效能。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-170">This increases performance during searches that do not use simple matching.</span></span>

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

<span data-ttu-id="fa8ff-171">此 Cmdlet 也會覆寫[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以處理使用者在命令列上建立的字串選擇。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="fa8ff-172">它會藉由呼叫私用**MatchString**方法，以自訂物件的形式寫入字串選取專案的結果。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

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

## <a name="accessing-content"></a><span data-ttu-id="fa8ff-173">存取內容</span><span class="sxs-lookup"><span data-stu-id="fa8ff-173">Accessing Content</span></span>

<span data-ttu-id="fa8ff-174">您的 Cmdlet 必須開啟 Windows PowerShell 路徑所指定的提供者，才能存取資料。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="fa8ff-175">系統會使用此執行時間的[Sessionstate](/dotnet/api/System.Management.Automation.SessionState)物件來存取提供者，而 Cmdlet 的[PSCmdlet. Invokeprovider \*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider)屬性則是用來開啟該提供者。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="fa8ff-176">藉由抓取開啟的提供者的[Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics)物件來存取內容。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="fa8ff-177">這個範例 Select-Str Cmdlet 會使用[Providerintrinsics. Content \*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content)屬性來公開要掃描的內容。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="fa8ff-178">然後，它可以呼叫[ContentCmdletproviderintrinsics. system.diagnostics.symbolstore.isymbolbinder1.getreader \*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader)方法，傳遞所需的 Windows PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fa8ff-179">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="fa8ff-179">Code Sample</span></span>

<span data-ttu-id="fa8ff-180">下列程式碼示範這個版本的 Select-Str Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="fa8ff-181">請注意，此程式碼包含 Cmdlet 類別、Cmdlet 所使用的私用方法，以及用來註冊 Cmdlet 的 Windows PowerShell 嵌入式管理單元程式碼。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="fa8ff-182">如需註冊 Cmdlet 的詳細資訊，請參閱[建立 Cmdlet](#defining-the-cmdlet-class)。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

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

## <a name="building-the-cmdlet"></a><span data-ttu-id="fa8ff-183">建立 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa8ff-183">Building the Cmdlet</span></span>

<span data-ttu-id="fa8ff-184">在執行 Cmdlet 之後，您必須透過 Windows powershell 嵌入式管理單元向 Windows PowerShell 註冊它。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="fa8ff-185">如需註冊 Cmdlet 的詳細資訊，請參閱[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="fa8ff-186">測試 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa8ff-186">Testing the Cmdlet</span></span>

<span data-ttu-id="fa8ff-187">當您的 Cmdlet 已向 Windows PowerShell 註冊時，您可以在命令列上執行它來進行測試。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="fa8ff-188">您可以使用下列程式來測試範例 Select-Str Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="fa8ff-189">啟動 Windows PowerShell，並使用 ".NET" 運算式來搜尋 Notes 檔案中是否有行出現。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="fa8ff-190">請注意，只有在路徑包含一個以上的單字時，才需要以引號括住路徑的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="fa8ff-191">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-191">The following output appears.</span></span>

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

2. <span data-ttu-id="fa8ff-192">搜尋 Notes 檔案中是否出現 "over" 一字，後面接著任何其他文字。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="fa8ff-193">`SimpleMatch`參數使用的預設值 `false` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="fa8ff-194">搜尋不區分大小寫，因為 `CaseSensitive` 參數設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="fa8ff-195">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-195">The following output appears.</span></span>

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

3. <span data-ttu-id="fa8ff-196">使用正則運算式作為模式來搜尋便箋檔案。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="fa8ff-197">Cmdlet 會搜尋以括弧括住的字母字元和空格。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="fa8ff-198">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-198">The following output appears.</span></span>

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

4. <span data-ttu-id="fa8ff-199">執行 Notes 檔案的區分大小寫搜尋，以尋找 "Parameter" 這個字。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="fa8ff-200">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-200">The following output appears.</span></span>

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

5. <span data-ttu-id="fa8ff-201">在 Windows PowerShell 隨附的變數提供者中，搜尋數值從0到9的變數。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="fa8ff-202">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="fa8ff-203">使用腳本區塊，在檔案 SelectStrCommandSample.cs 中搜尋字串 "Pos"。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="fa8ff-204">腳本的**cmatch**函數會執行不區分大小寫的模式比對。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="fa8ff-205">即會出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa8ff-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="fa8ff-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa8ff-206">See Also</span></span>

[<span data-ttu-id="fa8ff-207">如何建立 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa8ff-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="fa8ff-208">建立您的第一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa8ff-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="fa8ff-209">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fa8ff-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="fa8ff-210">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="fa8ff-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="fa8ff-211">[Windows PowerShell 的運作方式](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="fa8ff-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="fa8ff-212">[如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="fa8ff-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="fa8ff-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fa8ff-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
