---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 設定
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676609"
---
# <a name="dsc-configurations"></a><span data-ttu-id="3e67f-103">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="3e67f-103">DSC Configurations</span></span>

> <span data-ttu-id="3e67f-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3e67f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3e67f-105">DSC 設定是一種定義特殊類型函式的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3e67f-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="3e67f-106">若要定義設定，請使用 PowerShell 關鍵字 **Configuration**。</span><span class="sxs-lookup"><span data-stu-id="3e67f-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="3e67f-107">儲存指令碼做為`.ps1`檔案。</span><span class="sxs-lookup"><span data-stu-id="3e67f-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="3e67f-108">設定語法</span><span class="sxs-lookup"><span data-stu-id="3e67f-108">Configuration syntax</span></span>

<span data-ttu-id="3e67f-109">設定指令碼包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="3e67f-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="3e67f-110">**Configuration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="3e67f-110">The **Configuration** block.</span></span> <span data-ttu-id="3e67f-111">這是最外層的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="3e67f-111">This is the outermost script block.</span></span> <span data-ttu-id="3e67f-112">定義它的方式，是使用 **Configuration** 關鍵字並提供名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="3e67f-113">本例中的設定名稱是 "MyDscConfiguration"。</span><span class="sxs-lookup"><span data-stu-id="3e67f-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="3e67f-114">一個或多個 **Node** 區塊。</span><span class="sxs-lookup"><span data-stu-id="3e67f-114">One or more **Node** blocks.</span></span> <span data-ttu-id="3e67f-115">它們會定義您要設定的節點 (電腦或 VM)。</span><span class="sxs-lookup"><span data-stu-id="3e67f-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="3e67f-116">上述設定有一個 **Node** 區塊，以名為 "TEST-PC1" 的電腦為目標。</span><span class="sxs-lookup"><span data-stu-id="3e67f-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="3e67f-117">節點區塊可以接受多個電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="3e67f-118">一個或多個資源區塊。</span><span class="sxs-lookup"><span data-stu-id="3e67f-118">One or more resource blocks.</span></span> <span data-ttu-id="3e67f-119">設定就在這裡為它要設定的資源設定屬性。</span><span class="sxs-lookup"><span data-stu-id="3e67f-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="3e67f-120">本例有兩個資源區塊，兩個都呼叫 "WindowsFeature" 資源。</span><span class="sxs-lookup"><span data-stu-id="3e67f-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="3e67f-121">只要可以在 PowerShell 函式中執行的作業，通常在 **[設定]** 區塊內都可以執行。</span><span class="sxs-lookup"><span data-stu-id="3e67f-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="3e67f-122">例如，在前一個範例中，如果設定的目標電腦名稱不想使用硬式編碼，您可以為節點名稱加入參數：</span><span class="sxs-lookup"><span data-stu-id="3e67f-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="3e67f-123">在本範例中，您在編譯設定時將節點名稱當作 **ComputerName** 參數來傳遞，藉以指定節點名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="3e67f-124">預設名稱為 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="3e67f-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="3e67f-125">**節點**區塊也可以接受多個電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="3e67f-126">在上述範例中，您可以使用`-ComputerName`參數或傳遞的逗號分隔的電腦清單直接**節點**區塊。</span><span class="sxs-lookup"><span data-stu-id="3e67f-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="3e67f-127">指定的電腦清單時**節點**區塊中，從組態中，需要使用陣列標記法。</span><span class="sxs-lookup"><span data-stu-id="3e67f-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="3e67f-128">編譯設定</span><span class="sxs-lookup"><span data-stu-id="3e67f-128">Compiling the configuration</span></span>

<span data-ttu-id="3e67f-129">您必須先將設定編譯成 MOF 文件，才能施行設定。</span><span class="sxs-lookup"><span data-stu-id="3e67f-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="3e67f-130">呼叫設定即可完成此作業，就像您呼叫 PowerShell 函式一樣。</span><span class="sxs-lookup"><span data-stu-id="3e67f-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="3e67f-131">範例的最後一行僅包含設定名稱，並會呼叫設定。</span><span class="sxs-lookup"><span data-stu-id="3e67f-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="3e67f-132">若要呼叫設定，函式必須在全域範圍內 (像任何其他 PowerShell 函式一樣)。</span><span class="sxs-lookup"><span data-stu-id="3e67f-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="3e67f-133">執行此作業的方法有二：「點執行」指令碼，或使用 F5 或按一下 ISE 的 **[執行指令碼]** 按鈕執行設定指令碼。</span><span class="sxs-lookup"><span data-stu-id="3e67f-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="3e67f-134">若要點執行指令碼，請執行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含設定的指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="3e67f-135">當您呼叫設定時，它會：</span><span class="sxs-lookup"><span data-stu-id="3e67f-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="3e67f-136">解析所有的變數</span><span class="sxs-lookup"><span data-stu-id="3e67f-136">Resolves all variables</span></span>
- <span data-ttu-id="3e67f-137">在目前的目錄中建立和設定同名的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3e67f-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="3e67f-138">在新的目錄中建立名為 _NodeName_.mof 的檔案，其中 _NodeName_ 是設定的目標節點名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="3e67f-139">如果有多個節點，則將每個節點建立的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="3e67f-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="3e67f-140">MOF 檔案包含目標節點的所有設定資訊。</span><span class="sxs-lookup"><span data-stu-id="3e67f-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="3e67f-141">因為這樣，這個檔案的安全防護很重要。</span><span class="sxs-lookup"><span data-stu-id="3e67f-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="3e67f-142">如需詳細資訊，請參閱[保護 MOF 檔案](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="3e67f-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="3e67f-143">編譯上述第一個設定會導致下列的資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="3e67f-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="3e67f-144">如果設定使用參數，如同第二個範例，則必須在編譯時提供參數。</span><span class="sxs-lookup"><span data-stu-id="3e67f-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="3e67f-145">它看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="3e67f-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="3e67f-146">在設定中使用新的資源</span><span class="sxs-lookup"><span data-stu-id="3e67f-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="3e67f-147">如果執行了前面的範例，您可能會注意到，系統警告使用了未明確匯入的資源。</span><span class="sxs-lookup"><span data-stu-id="3e67f-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="3e67f-148">現在，DSC 在 PSDesiredStateConfiguration 模組中附有 12 種資源。</span><span class="sxs-lookup"><span data-stu-id="3e67f-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="3e67f-149">Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 可用於決定在系統上安裝並供 LCM 使用的資源。</span><span class="sxs-lookup"><span data-stu-id="3e67f-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="3e67f-150">這些模組放置在 `$env:PSModulePath` 並由 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 正確辨識後，仍需要載入至設定中。</span><span class="sxs-lookup"><span data-stu-id="3e67f-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="3e67f-151">**Import-dscresource**只有在內才能辨識為動態關鍵字**組態**區塊中，不是 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e67f-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="3e67f-152">**Import-DscResource** 支援兩個參數：</span><span class="sxs-lookup"><span data-stu-id="3e67f-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="3e67f-153">**ModuleName**，使用 **Import-DscResource** 時建議用它。</span><span class="sxs-lookup"><span data-stu-id="3e67f-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="3e67f-154">它接受包含了要匯入資源 (以及模組名稱字串陣列) 的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="3e67f-155">**Name** 是要匯入的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67f-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="3e67f-156">[Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 傳回的 "Name" 不是易記的名稱，而是定義資源結構描述時使用的類別名稱 ([Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 傳回 **ResourceType**)。</span><span class="sxs-lookup"><span data-stu-id="3e67f-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="3e67f-157">如需有關使用`Import-DSCResource`，請參閱[使用 Import-dscresource](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="3e67f-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="3e67f-158">PowerShell v4 和 v5 的差異</span><span class="sxs-lookup"><span data-stu-id="3e67f-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="3e67f-159">有差異，需要儲存在 PowerShell 4.0 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="3e67f-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="3e67f-160">如需詳細資訊，請參閱 <<c0> [ 資源位置](import-dscresource.md#resource-location)。</span><span class="sxs-lookup"><span data-stu-id="3e67f-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e67f-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e67f-161">See Also</span></span>

- [<span data-ttu-id="3e67f-162">Windows PowerShell 預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="3e67f-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="3e67f-163">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="3e67f-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="3e67f-164">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="3e67f-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
