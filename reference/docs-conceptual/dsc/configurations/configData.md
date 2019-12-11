---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用設定資料
ms.openlocfilehash: 7d13b19ba932d1a818194a221f145fd1a3832547
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954185"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="b3e70-103">使用 DSC 中的設定資料</span><span class="sxs-lookup"><span data-stu-id="b3e70-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="b3e70-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b3e70-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b3e70-105">您可以使用內建的 DSC **ConfigurationData** 參數，定義可用於設定中的資料。</span><span class="sxs-lookup"><span data-stu-id="b3e70-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="b3e70-106">這可讓您建立可用於多個節點或不同環境的單一設定。</span><span class="sxs-lookup"><span data-stu-id="b3e70-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="b3e70-107">例如，如果您要開發應用程式，您可以針對開發和生產環境使用一個設定，並使用設定資料來指定每個環境的資料。</span><span class="sxs-lookup"><span data-stu-id="b3e70-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="b3e70-108">本主題將說明 **ConfigurationData** 雜湊表的結構。</span><span class="sxs-lookup"><span data-stu-id="b3e70-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="b3e70-109">如需如何使用設定資料的範例，請參閱[分離設定和環境資料](separatingEnvData.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e70-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="b3e70-110">ConfigurationData 一般參數</span><span class="sxs-lookup"><span data-stu-id="b3e70-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="b3e70-111">DSC 設定採用 **ConfigurationData** 一般參數，這是編譯設定時所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="b3e70-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="b3e70-112">如需編譯設定的資訊，請參閱 [DSC 設定](configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e70-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="b3e70-113">**ConfigurationData** 參數是至少必須有一個名為 **AllNodes** 之索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b3e70-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="b3e70-114">它也可以包含一或多個其他索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b3e70-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="b3e70-115">本主題中的範例使用名為 `NonNodeData` 的單一額外索引鍵 (而不是具名 **AllNodes** 索引鍵)，但是您可以包含任意數目的額外索引鍵，並將它們任意命名。</span><span class="sxs-lookup"><span data-stu-id="b3e70-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="b3e70-116">**AllNodes** 索引鍵的值是陣列。</span><span class="sxs-lookup"><span data-stu-id="b3e70-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="b3e70-117">此陣列的每個元素也是至少必須有一個名為 **NodeName** 之索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="b3e70-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="b3e70-118">您也可以將其他索引鍵新增至每個雜湊表：</span><span class="sxs-lookup"><span data-stu-id="b3e70-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="b3e70-119">若要將屬性套用至所有節點，您可以建立 **AllNodes** 陣列的成員，其 **NodeName** 為 `*`。</span><span class="sxs-lookup"><span data-stu-id="b3e70-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="b3e70-120">例如，您可以如下為每個節點提供 `LogPath` 屬性：</span><span class="sxs-lookup"><span data-stu-id="b3e70-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="b3e70-121">這相當於將名稱為 `LogPath` 且值為 `"C:\Logs"` 的屬性新增至每個其他區塊 (`VM-1`、`VM-2` 和 `VM-3`)。</span><span class="sxs-lookup"><span data-stu-id="b3e70-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="b3e70-122">定義 ConfigurationData 雜湊表</span><span class="sxs-lookup"><span data-stu-id="b3e70-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="b3e70-123">您可以將 **ConfigurationData** 定義為與設定位於相同指令碼檔內的變數 (如上述範例)，或個別 `.psd1` 檔案中的變數。</span><span class="sxs-lookup"><span data-stu-id="b3e70-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="b3e70-124">若要在 `.psd1` 檔案中定義 **ConfigurationData**，請建立只包含代表設定資料之雜湊表的檔案。</span><span class="sxs-lookup"><span data-stu-id="b3e70-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="b3e70-125">例如，您可以建立具有下列內容的檔案，並命名為 `MyData.psd1`：</span><span class="sxs-lookup"><span data-stu-id="b3e70-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="b3e70-126">編譯具有設定資料的設定</span><span class="sxs-lookup"><span data-stu-id="b3e70-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="b3e70-127">若要編譯您已為其定義設定資料的設定，請將設定資料當作 **ConfigurationData** 參數的值來傳遞。</span><span class="sxs-lookup"><span data-stu-id="b3e70-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="b3e70-128">這會為 **AllNodes** 陣列中的每個項目建立一個 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3e70-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="b3e70-129">每個 MOF 檔案都會以對應之陣列項目的 `NodeName` 屬性來命名。</span><span class="sxs-lookup"><span data-stu-id="b3e70-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="b3e70-130">例如，如果您依上述 `MyData.psd1` 檔案中的方式定義設定資料，則編譯設定將會同時建立 `VM-1.mof` 和 `VM-2.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3e70-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="b3e70-131">使用變數來編譯具有設定資料的設定</span><span class="sxs-lookup"><span data-stu-id="b3e70-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="b3e70-132">若要使用定義為與設定位於相同 `.ps1` 檔案中之變數的設定資料，請在編譯設定時，將該變數名稱當作 **ConfigurationData** 參數的值來傳遞：</span><span class="sxs-lookup"><span data-stu-id="b3e70-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="b3e70-133">使用資料檔來編譯具有設定資料的設定</span><span class="sxs-lookup"><span data-stu-id="b3e70-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="b3e70-134">若要使用在 .psd1 檔案中定義的設定資料，您可以在編譯設定時，傳遞該檔案的路徑和名稱作為 **ConfigurationData** 參數值：</span><span class="sxs-lookup"><span data-stu-id="b3e70-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="b3e70-135">在設定中使用 ConfigurationData 變數</span><span class="sxs-lookup"><span data-stu-id="b3e70-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="b3e70-136">DSC 提供下列特殊變數，可用於設定指令碼中︰</span><span class="sxs-lookup"><span data-stu-id="b3e70-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="b3e70-137">**$AllNodes** 代表 **ConfigurationData** 中所定義的整個節點集合。</span><span class="sxs-lookup"><span data-stu-id="b3e70-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="b3e70-138">您可以使用 **.Where()** 和 **.ForEach()** 篩選 **AllNodes** 集合。</span><span class="sxs-lookup"><span data-stu-id="b3e70-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="b3e70-139">**ConfigurationData** 代表編譯設定時，當做參數傳遞的整個雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b3e70-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="b3e70-140">**MyTypeName** 包含變數所用的[設定](configurations.md)名稱。</span><span class="sxs-lookup"><span data-stu-id="b3e70-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="b3e70-141">例如，在設定 `MyDscConfiguration` 中，`$MyTypeName` 的值為 `MyDscConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="b3e70-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="b3e70-142">**Node** 代表 **AllNodes** 集合使用 **.Where()** 或 **.ForEach()** 篩選後所包含的特定項目。</span><span class="sxs-lookup"><span data-stu-id="b3e70-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="b3e70-143">您可以在 [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays) 中深入閱讀這些方法</span><span class="sxs-lookup"><span data-stu-id="b3e70-143">You can read more about these methods in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="b3e70-144">使用非節點資料</span><span class="sxs-lookup"><span data-stu-id="b3e70-144">Using non-node data</span></span>

<span data-ttu-id="b3e70-145">如我們在先前的範例中所見，**ConfigurationData** 雜湊表除了必要的 **AllNodes** 索引鍵之外，還可以有一或多個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b3e70-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="b3e70-146">在本主題的範例中，我們只使用了單一額外節點，並將它命名為 `NonNodeData`。</span><span class="sxs-lookup"><span data-stu-id="b3e70-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="b3e70-147">不過，您可以定義任何數目的額外索引鍵，並將它們任意命名。</span><span class="sxs-lookup"><span data-stu-id="b3e70-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="b3e70-148">如需有關使用非節點資料的範例，請參閱[分離設定和環境資料](separatingEnvData.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e70-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e70-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3e70-149">See Also</span></span>

- [<span data-ttu-id="b3e70-150">設定資料的認證選項</span><span class="sxs-lookup"><span data-stu-id="b3e70-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="b3e70-151">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="b3e70-151">DSC Configurations</span></span>](configurations.md)