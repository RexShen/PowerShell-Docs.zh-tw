---
ms.date: 12/12/2018
keywords: dsc, powershell, 資源, 資源庫, 安裝, 設定
title: 將參數新增至設定
ms.openlocfilehash: 9aa4c746042e89d7767e1b326233dcca1e5c4c24
ms.sourcegitcommit: b80ce0396550d0896189d0205d6c4b4372ac2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141408"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="30f40-103">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="30f40-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="30f40-104">就像函式一樣，您可以將[設定](configurations.md)參數化，根據使用者輸入來進行更動態的設定。</span><span class="sxs-lookup"><span data-stu-id="30f40-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="30f40-105">步驟類似於[使用參數的函式](/powershell/module/microsoft.powershell.core/about/about_functions)中所描述。</span><span class="sxs-lookup"><span data-stu-id="30f40-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="30f40-106">此範例從基本的 Configuration 開始，其將 "Spooler" 服務設定為 "Running"。</span><span class="sxs-lookup"><span data-stu-id="30f40-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="30f40-107">內建 Configuration 參數</span><span class="sxs-lookup"><span data-stu-id="30f40-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="30f40-108">與函式不同，[CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) 屬性不會新增任何功能。</span><span class="sxs-lookup"><span data-stu-id="30f40-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="30f40-109">除了[一般參數](/powershell/module/microsoft.powershell.core/about/about_commonparameters)之外，Configuration 也能夠使用下列內建參數，您不需要定義它們。</span><span class="sxs-lookup"><span data-stu-id="30f40-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|        <span data-ttu-id="30f40-110">參數</span><span class="sxs-lookup"><span data-stu-id="30f40-110">Parameter</span></span>        |                                         <span data-ttu-id="30f40-111">描述</span><span class="sxs-lookup"><span data-stu-id="30f40-111">Description</span></span>                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | <span data-ttu-id="30f40-112">用於定義[複合設定](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="30f40-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-DependsOn`            | <span data-ttu-id="30f40-113">用於定義[複合設定](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="30f40-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-PSDSCRunAsCredential` | <span data-ttu-id="30f40-114">用於定義[複合設定](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="30f40-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>                             |
| `-ConfigurationData`    | <span data-ttu-id="30f40-115">用於傳遞在 Configuration 中使用的結構化[設定資料](configData.md)。</span><span class="sxs-lookup"><span data-stu-id="30f40-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span> |
| `-OutputPath`           | <span data-ttu-id="30f40-116">用於指定將要編譯的 "\<computername\>.mof" 檔案位置</span><span class="sxs-lookup"><span data-stu-id="30f40-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>                      |

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="30f40-117">將自己的參數加入 Configuration</span><span class="sxs-lookup"><span data-stu-id="30f40-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="30f40-118">除了內建參數之外，您還可以將自己的參數加入到 Configuration。</span><span class="sxs-lookup"><span data-stu-id="30f40-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span>
<span data-ttu-id="30f40-119">參數區塊直接位於 Configuration 宣告內，就和 Function 一樣。</span><span class="sxs-lookup"><span data-stu-id="30f40-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="30f40-120">Configuration 的參數區塊應該在任何的 **Node** 宣告之外，並且位於任何 *import* 陳述式上方。</span><span class="sxs-lookup"><span data-stu-id="30f40-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="30f40-121">您可藉由加入參數讓自己的 Configuration 更穩定且具動態性。</span><span class="sxs-lookup"><span data-stu-id="30f40-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="30f40-122">加入 ComputerName 參數</span><span class="sxs-lookup"><span data-stu-id="30f40-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="30f40-123">您可以加入的第一個參數是 `-Computername` 參數，如此您就能夠以動態方式針對任何傳遞到設定中的 `-Computername` 編譯 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="30f40-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="30f40-124">和函式一樣，您也可以定義預設值，以防使用者並未傳入 `-ComputerName` 的值</span><span class="sxs-lookup"><span data-stu-id="30f40-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="30f40-125">在您的設定中，您之後可以在定義 Node 區塊時指定自己的 `-ComputerName` 參數。</span><span class="sxs-lookup"><span data-stu-id="30f40-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="30f40-126">使用參數呼叫 Configuration</span><span class="sxs-lookup"><span data-stu-id="30f40-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="30f40-127">在將參數加入到 Configuration 之後，您就可以像使用 Cmdlet般使用它們。</span><span class="sxs-lookup"><span data-stu-id="30f40-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="30f40-128">編譯多個.mof 檔案</span><span class="sxs-lookup"><span data-stu-id="30f40-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="30f40-129">Node 區塊也可接受以逗號分隔的電腦名稱清單，並且會為每個電腦名稱產生 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="30f40-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="30f40-130">您可以執行下列範例，來為傳遞至 `-ComputerName` 參數的所有電腦產生 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="30f40-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String[]]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="30f40-131">Configuration 中的進階參數</span><span class="sxs-lookup"><span data-stu-id="30f40-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="30f40-132">除了 `-ComputerName` 參數以外，我們還可以加入服務名稱和狀態的參數。</span><span class="sxs-lookup"><span data-stu-id="30f40-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span>
<span data-ttu-id="30f40-133">下列範例區塊會加入具有 `-ServiceName` 參數的參數區塊，並使用它以動態方式定義 **Service** 資源區塊。</span><span class="sxs-lookup"><span data-stu-id="30f40-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="30f40-134">還會加入 `-State` 參數以動態方式定義 **Service** 資源區塊中的 **State**。</span><span class="sxs-lookup"><span data-stu-id="30f40-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="30f40-135">在更進一步的範例中，將您的動態資料移至結構化的[設定資料中](configData.md)可能較為合理。</span><span class="sxs-lookup"><span data-stu-id="30f40-135">In more advanced scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="30f40-136">範例 Configuration 現在會採用動態的 `$ServiceName`，但若它並未被指定，編譯結果會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="30f40-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="30f40-137">您可以如這個範例般加入預設值。</span><span class="sxs-lookup"><span data-stu-id="30f40-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="30f40-138">在本範例中，直接強制使用者指定 `$ServiceName` 參數的值比較合理。</span><span class="sxs-lookup"><span data-stu-id="30f40-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="30f40-139">`parameter` 屬性可讓您將更增進一步的驗證和管線支援加入到 Configuration 的參數。</span><span class="sxs-lookup"><span data-stu-id="30f40-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="30f40-140">在以上任何的參數宣告中加入 `parameter` 屬性區塊，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30f40-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="30f40-141">您可以將引數指定到每個 `parameter` 屬性，來控制所定義之參數的各層面。</span><span class="sxs-lookup"><span data-stu-id="30f40-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="30f40-142">下列範例會使 `$ServiceName` 成為**強制**參數。</span><span class="sxs-lookup"><span data-stu-id="30f40-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="30f40-143">對於 `$State` 參數，我們想防止使用者指定預先定義值組 (例如 Running、Stopped) 以外的值，而 `ValidationSet*` 屬性將可防止使用者指定預先定義值組 (例如 Running、Stopped) 以外的值。</span><span class="sxs-lookup"><span data-stu-id="30f40-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="30f40-144">下列範例會將 `ValidationSet` 屬性加入 `$State` 參數。</span><span class="sxs-lookup"><span data-stu-id="30f40-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="30f40-145">由於我們不想讓 `$State` 參數成為**強制**參數，我們必須為它加入預設值。</span><span class="sxs-lookup"><span data-stu-id="30f40-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="30f40-146">當使用 `parameter` 屬性時，您不需要指定 `validation` 屬性。</span><span class="sxs-lookup"><span data-stu-id="30f40-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="30f40-147">您可以在 `parameter`about_Functions_Advanced_Parameters[ 中深入了解 ](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters) 和 validation 屬性。</span><span class="sxs-lookup"><span data-stu-id="30f40-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="30f40-148">完全參數化的 Configuration</span><span class="sxs-lookup"><span data-stu-id="30f40-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="30f40-149">我們現在有參數化的 Configuration，可強制使用者指定 `-InstanceName`、`-ServiceName`，並驗證 `-State` 參數。</span><span class="sxs-lookup"><span data-stu-id="30f40-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="30f40-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30f40-150">See also</span></span>

- [<span data-ttu-id="30f40-151">撰寫 DSC 設定的說明</span><span class="sxs-lookup"><span data-stu-id="30f40-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="30f40-152">動態設定</span><span class="sxs-lookup"><span data-stu-id="30f40-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="30f40-153">在設定中使用設定資料</span><span class="sxs-lookup"><span data-stu-id="30f40-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="30f40-154">分離設定與環境資料</span><span class="sxs-lookup"><span data-stu-id="30f40-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
