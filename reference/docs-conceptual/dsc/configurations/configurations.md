---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 設定
description: DSC 設定是一種定義特殊類型函式的 PowerShell 指令碼。
ms.openlocfilehash: e59ad2791055ee3ff0150c342ec621d0228c4fc1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658567"
---
# <a name="dsc-configurations"></a><span data-ttu-id="d9d36-104">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="d9d36-104">DSC Configurations</span></span>

> <span data-ttu-id="d9d36-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d9d36-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d9d36-106">DSC 設定是一種定義特殊類型函式的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d9d36-106">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="d9d36-107">若要定義設定，請使用 PowerShell 關鍵字 **Configuration** 。</span><span class="sxs-lookup"><span data-stu-id="d9d36-107">To define a configuration, you use the PowerShell keyword **Configuration** .</span></span>

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

<span data-ttu-id="d9d36-108">將指令碼儲存為 `.ps1` 檔案。</span><span class="sxs-lookup"><span data-stu-id="d9d36-108">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="d9d36-109">設定語法</span><span class="sxs-lookup"><span data-stu-id="d9d36-109">Configuration syntax</span></span>

<span data-ttu-id="d9d36-110">設定指令碼包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="d9d36-110">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="d9d36-111">**Configuration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="d9d36-111">The **Configuration** block.</span></span> <span data-ttu-id="d9d36-112">這是最外層的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="d9d36-112">This is the outermost script block.</span></span> <span data-ttu-id="d9d36-113">定義它的方式，是使用 **Configuration** 關鍵字並提供名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-113">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="d9d36-114">本例中的設定名稱是 "MyDscConfiguration"。</span><span class="sxs-lookup"><span data-stu-id="d9d36-114">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="d9d36-115">一個或多個 **Node** 區塊。</span><span class="sxs-lookup"><span data-stu-id="d9d36-115">One or more **Node** blocks.</span></span> <span data-ttu-id="d9d36-116">它們會定義您要設定的節點 (電腦或 VM)。</span><span class="sxs-lookup"><span data-stu-id="d9d36-116">These define the nodes (computers or VMs) that you are configuring.</span></span>
  <span data-ttu-id="d9d36-117">上述設定有一個 **Node** 區塊，以名為 "TEST-PC1" 的電腦為目標。</span><span class="sxs-lookup"><span data-stu-id="d9d36-117">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
  <span data-ttu-id="d9d36-118">節點區塊可以接受多個電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-118">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="d9d36-119">一個或多個資源區塊。</span><span class="sxs-lookup"><span data-stu-id="d9d36-119">One or more resource blocks.</span></span> <span data-ttu-id="d9d36-120">設定就在這裡為它要設定的資源設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d9d36-120">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="d9d36-121">本例有兩個資源區塊，兩個都呼叫 "WindowsFeature" 資源。</span><span class="sxs-lookup"><span data-stu-id="d9d36-121">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="d9d36-122">只要可以在 PowerShell 函式中執行的作業，通常在 **[設定]** 區塊內都可以執行。</span><span class="sxs-lookup"><span data-stu-id="d9d36-122">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="d9d36-123">例如，在前一個範例中，如果設定的目標電腦名稱不想使用硬式編碼，您可以為節點名稱加入參數：</span><span class="sxs-lookup"><span data-stu-id="d9d36-123">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="d9d36-124">在本範例中，您在編譯設定時將節點名稱當作 **ComputerName** 參數來傳遞，藉以指定節點名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-124">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="d9d36-125">預設名稱為 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="d9d36-125">The name defaults to "localhost".</span></span>

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

<span data-ttu-id="d9d36-126">**節點** 區塊也可以接受多個電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-126">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="d9d36-127">在上述範例中，您可以使用 `-ComputerName` 參數，也可以將逗號分隔的電腦清單直接傳遞給 **節點** 區塊。</span><span class="sxs-lookup"><span data-stu-id="d9d36-127">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="d9d36-128">在 **節點** 區塊中指定電腦清單時，從設定中，您需要使用陣列標記法。</span><span class="sxs-lookup"><span data-stu-id="d9d36-128">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

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

## <a name="compiling-the-configuration"></a><span data-ttu-id="d9d36-129">編譯設定</span><span class="sxs-lookup"><span data-stu-id="d9d36-129">Compiling the configuration</span></span>

<span data-ttu-id="d9d36-130">您必須先將設定編譯成 MOF 文件，才能施行設定。</span><span class="sxs-lookup"><span data-stu-id="d9d36-130">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="d9d36-131">呼叫設定即可完成此作業，就像您呼叫 PowerShell 函式一樣。</span><span class="sxs-lookup"><span data-stu-id="d9d36-131">You do this by calling the configuration like you would call a PowerShell function.</span></span> <span data-ttu-id="d9d36-132">範例的最後一行僅包含設定名稱，並會呼叫設定。</span><span class="sxs-lookup"><span data-stu-id="d9d36-132">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="d9d36-133">若要呼叫設定，函式必須在全域範圍內 (像任何其他 PowerShell 函式一樣)。</span><span class="sxs-lookup"><span data-stu-id="d9d36-133">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> <span data-ttu-id="d9d36-134">執行此作業的方法有二：「點執行」指令碼，或使用 F5 或按一下 ISE 的 **[執行指令碼]** 按鈕執行設定指令碼。</span><span class="sxs-lookup"><span data-stu-id="d9d36-134">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> <span data-ttu-id="d9d36-135">若要點執行指令碼，請執行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含設定的指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-135">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="d9d36-136">當您呼叫設定時，它會：</span><span class="sxs-lookup"><span data-stu-id="d9d36-136">When you call the configuration, it:</span></span>

- <span data-ttu-id="d9d36-137">解析所有的變數</span><span class="sxs-lookup"><span data-stu-id="d9d36-137">Resolves all variables</span></span>
- <span data-ttu-id="d9d36-138">在目前的目錄中建立和設定同名的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d9d36-138">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="d9d36-139">在新的目錄中建立名為 _NodeName_ .mof 的檔案，其中 _NodeName_ 是設定的目標節點名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-139">Creates a file named _NodeName_ .mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> <span data-ttu-id="d9d36-140">如果有多個節點，每個節點都會建立一個 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="d9d36-140">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="d9d36-141">MOF 檔案包含目標節點的所有設定資訊。</span><span class="sxs-lookup"><span data-stu-id="d9d36-141">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="d9d36-142">因為這樣，這個檔案的安全防護很重要。</span><span class="sxs-lookup"><span data-stu-id="d9d36-142">Because of this, it's important to keep it secure.</span></span> <span data-ttu-id="d9d36-143">如需詳細資訊，請參閱[保護 MOF 檔案](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="d9d36-143">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="d9d36-144">編譯上述第一個設定會導致下列的資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="d9d36-144">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="d9d36-145">如果設定使用參數，如同第二個範例，則必須在編譯時提供參數。</span><span class="sxs-lookup"><span data-stu-id="d9d36-145">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="d9d36-146">它看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="d9d36-146">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="d9d36-147">在設定中使用新的資源</span><span class="sxs-lookup"><span data-stu-id="d9d36-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="d9d36-148">如果執行了前面的範例，您可能會注意到，系統警告使用了未明確匯入的資源。</span><span class="sxs-lookup"><span data-stu-id="d9d36-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span> <span data-ttu-id="d9d36-149">現在，DSC 在 PSDesiredStateConfiguration 模組中附有 12 種資源。</span><span class="sxs-lookup"><span data-stu-id="d9d36-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="d9d36-150">Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 可用於決定在系統上安裝並供 LCM 使用的資源。</span><span class="sxs-lookup"><span data-stu-id="d9d36-150">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="d9d36-151">這些模組放置在 `$env:PSModulePath` 並由 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 正確辨識後，仍需要載入至設定中。</span><span class="sxs-lookup"><span data-stu-id="d9d36-151">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="d9d36-152">**Import-DscResource** 是只能在 **設定** 區塊中辨識的動態關鍵字，它不是 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d9d36-152">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span> <span data-ttu-id="d9d36-153">**Import-DscResource** 支援兩個參數：</span><span class="sxs-lookup"><span data-stu-id="d9d36-153">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="d9d36-154">**ModuleName** ，使用 **Import-DscResource** 時建議用它。</span><span class="sxs-lookup"><span data-stu-id="d9d36-154">**ModuleName** is the recommended way of using **Import-DscResource** .</span></span> <span data-ttu-id="d9d36-155">它接受包含了要匯入資源 (以及模組名稱字串陣列) 的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-155">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="d9d36-156">**Name** 是要匯入的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="d9d36-156">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="d9d36-157">[Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 傳回的 "Name" 不是易記的名稱，而是定義資源結構描述時使用的類別名稱 ( [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 傳回 **ResourceType** )。</span><span class="sxs-lookup"><span data-stu-id="d9d36-157">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="d9d36-158">如需使用 `Import-DSCResource` 的詳細資訊，請參閱[使用 Import-DSCResource](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="d9d36-158">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d9d36-159">PowerShell v4 和 v5 的差異</span><span class="sxs-lookup"><span data-stu-id="d9d36-159">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d9d36-160">在 PowerShell 4.0 中需要儲存 DSC 資源的位置存在差異。</span><span class="sxs-lookup"><span data-stu-id="d9d36-160">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="d9d36-161">如需詳細資訊，請參閱[資源位置](import-dscresource.md#resource-location)。</span><span class="sxs-lookup"><span data-stu-id="d9d36-161">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d36-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9d36-162">See Also</span></span>

- [<span data-ttu-id="d9d36-163">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="d9d36-163">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="d9d36-164">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d9d36-164">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="d9d36-165">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="d9d36-165">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
