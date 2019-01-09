---
ms.date: 12/12/2018
keywords: dsc，powershell、 資源、 資源庫、 安裝程式
title: 將參數新增至設定
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400715"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="0be0b-103">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="0be0b-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="0be0b-104">函數，類似[組態](configurations.md)一種可以參數化，以允許更多動態組態，根據使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="0be0b-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="0be0b-105">中所描述的步驟大致[具有參數的函式](/powershell/module/microsoft.powershell.core/about/about_functions)。</span><span class="sxs-lookup"><span data-stu-id="0be0b-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="0be0b-106">此範例會啟動基本的設定會設定為 「 執行 」 的 「 多工緩衝處理器 」 服務。</span><span class="sxs-lookup"><span data-stu-id="0be0b-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="0be0b-107">內建的組態參數</span><span class="sxs-lookup"><span data-stu-id="0be0b-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="0be0b-108">不同於函式， [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)屬性新增任何功能。</span><span class="sxs-lookup"><span data-stu-id="0be0b-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="0be0b-109">除了[一般參數](/powershell/module/microsoft.powershell.core/about/about_commonparameters)，組態也可以使用下列內建參數，而不需要您定義它們。</span><span class="sxs-lookup"><span data-stu-id="0be0b-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="0be0b-110">參數</span><span class="sxs-lookup"><span data-stu-id="0be0b-110">Parameter</span></span>  |<span data-ttu-id="0be0b-111">描述</span><span class="sxs-lookup"><span data-stu-id="0be0b-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="0be0b-112">用於定義[複合設定](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="0be0b-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="0be0b-113">用於定義[複合設定](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="0be0b-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="0be0b-114">用於定義[複合設定](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="0be0b-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="0be0b-115">用來將傳遞的結構化[組態資料](configData.md)組態中使用。</span><span class="sxs-lookup"><span data-stu-id="0be0b-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="0be0b-116">用來指定的位置，您 「\<computername\>.mof"檔案將會編譯</span><span class="sxs-lookup"><span data-stu-id="0be0b-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="0be0b-117">將您自己的參數新增至組態</span><span class="sxs-lookup"><span data-stu-id="0be0b-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="0be0b-118">除了內建的參數，您也可以新增您自己的參數到您的設定。</span><span class="sxs-lookup"><span data-stu-id="0be0b-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="0be0b-119">在參數區塊會直接在設定宣告，就像函式。</span><span class="sxs-lookup"><span data-stu-id="0be0b-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="0be0b-120">設定參數區塊應該是任何外部**節點**宣告，及任何上面*匯入*陳述式。</span><span class="sxs-lookup"><span data-stu-id="0be0b-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="0be0b-121">新增參數，您可以在更穩定且動態進行您的設定。</span><span class="sxs-lookup"><span data-stu-id="0be0b-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="0be0b-122">將 ComputerName 參數</span><span class="sxs-lookup"><span data-stu-id="0be0b-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="0be0b-123">您可以新增第一個參數是`-Computername`參數，讓您以動態方式可以編譯 「.mof 」 檔案的任何`-Computername`您傳遞給您的設定。</span><span class="sxs-lookup"><span data-stu-id="0be0b-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="0be0b-124">例如函式中，您也可以定義預設值，如果使用者未通過的值 `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="0be0b-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="0be0b-125">在您的設定，然後您可以指定您`-ComputerName`參數定義您的節點區塊時。</span><span class="sxs-lookup"><span data-stu-id="0be0b-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="0be0b-126">呼叫您的組態參數</span><span class="sxs-lookup"><span data-stu-id="0be0b-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="0be0b-127">您已將參數加入到您的組態之後，您可以使用它們，就像您使用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0be0b-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="0be0b-128">編譯多個.mof 檔案</span><span class="sxs-lookup"><span data-stu-id="0be0b-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="0be0b-129">節點區塊也可接受電腦名稱的逗號分隔的清單，並會針對每個產生 「.mof 」 檔案。</span><span class="sxs-lookup"><span data-stu-id="0be0b-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="0be0b-130">您可以執行下列範例產生的所有電腦傳遞至 「.mof"檔案`-ComputerName`參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="0be0b-131">在組態中的進階的參數</span><span class="sxs-lookup"><span data-stu-id="0be0b-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="0be0b-132">除了`-ComputerName`參數，我們可以新增的服務名稱和狀態的參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="0be0b-133">下列範例會將參數區塊`-ServiceName`參數並使用它來動態定義**服務**資源區塊。</span><span class="sxs-lookup"><span data-stu-id="0be0b-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="0be0b-134">它也會新增`-State`參數來動態定義**狀態**中**服務**資源區塊。</span><span class="sxs-lookup"><span data-stu-id="0be0b-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
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
> <span data-ttu-id="0be0b-135">在多個 advacned 案例中，它可能會讓您動態的資料移至結構化比較合理[組態資料](configData.md)。</span><span class="sxs-lookup"><span data-stu-id="0be0b-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="0be0b-136">範例組態現在會採用動態`$ServiceName`，但如果未指定其中一個項目，則編譯會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0be0b-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="0be0b-137">您可以新增如下列範例的預設值。</span><span class="sxs-lookup"><span data-stu-id="0be0b-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="0be0b-138">在本例中，它比較理想的只會強制使用者指定的值`$ServiceName`參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="0be0b-139">`parameter`屬性可讓您將進一步的驗證和管線支援新增至您的組態參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="0be0b-140">以上任何參數宣告中，新增`parameter`屬性區塊，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0be0b-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="0be0b-141">您可以指定每個引數`parameter`屬性，以控制定義參數的各個層面。</span><span class="sxs-lookup"><span data-stu-id="0be0b-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="0be0b-142">下列範例會使`$ServiceName`**強制**參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="0be0b-143">針對`$State`參數，我們想要防止使用者指定一組預先定義以外的值 （例如執行中、 已停止）`ValidationSet*`屬性會防止使用者指定一組預先定義 （例如執行中、 以外的值已停止）。</span><span class="sxs-lookup"><span data-stu-id="0be0b-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="0be0b-144">下列範例會將`ValidationSet`屬性設定為`$State`參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="0be0b-145">因為我們不想要`$State`參數**強制**，我們需要加入它的預設值。</span><span class="sxs-lookup"><span data-stu-id="0be0b-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="0be0b-146">您不需要指定`parameter`屬性使用時`validation`屬性。</span><span class="sxs-lookup"><span data-stu-id="0be0b-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="0be0b-147">您可以深入了解`parameter`和驗證屬性中的[about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0be0b-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="0be0b-148">完全參數化的設定</span><span class="sxs-lookup"><span data-stu-id="0be0b-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="0be0b-149">我們現在有會強制使用者在指定的參數化的組態`-InstanceName`， `-ServiceName`，並驗證`-State`參數。</span><span class="sxs-lookup"><span data-stu-id="0be0b-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0be0b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0be0b-150">See also</span></span>

- [<span data-ttu-id="0be0b-151">撰寫 DSC 設定的說明</span><span class="sxs-lookup"><span data-stu-id="0be0b-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="0be0b-152">動態組態</span><span class="sxs-lookup"><span data-stu-id="0be0b-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="0be0b-153">使用您的組態中的組態資料</span><span class="sxs-lookup"><span data-stu-id="0be0b-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="0be0b-154">個別的設定和環境資料</span><span class="sxs-lookup"><span data-stu-id="0be0b-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
