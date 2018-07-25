---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 設定
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093689"
---
# <a name="dsc-configurations"></a><span data-ttu-id="50d72-103">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="50d72-103">DSC Configurations</span></span>

> <span data-ttu-id="50d72-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="50d72-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="50d72-105">DSC 設定是一種定義特殊類型函式的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="50d72-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="50d72-106">若要定義設定，請使用 PowerShell 關鍵字 **Configuration**。</span><span class="sxs-lookup"><span data-stu-id="50d72-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

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

<span data-ttu-id="50d72-107">將指令碼儲存為 .ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="50d72-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="50d72-108">設定語法</span><span class="sxs-lookup"><span data-stu-id="50d72-108">Configuration syntax</span></span>

<span data-ttu-id="50d72-109">設定指令碼包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="50d72-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="50d72-110">**Configuration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="50d72-110">The **Configuration** block.</span></span> <span data-ttu-id="50d72-111">這是最外層的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="50d72-111">This is the outermost script block.</span></span> <span data-ttu-id="50d72-112">定義它的方式，是使用 **Configuration** 關鍵字並提供名稱。</span><span class="sxs-lookup"><span data-stu-id="50d72-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="50d72-113">本例中的設定名稱是 "MyDscConfiguration"。</span><span class="sxs-lookup"><span data-stu-id="50d72-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="50d72-114">一個或多個 **Node** 區塊。</span><span class="sxs-lookup"><span data-stu-id="50d72-114">One or more **Node** blocks.</span></span> <span data-ttu-id="50d72-115">它們會定義您要設定的節點 (電腦或 VM)。</span><span class="sxs-lookup"><span data-stu-id="50d72-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="50d72-116">上述設定有一個 **Node** 區塊，以名為 "TEST-PC1" 的電腦為目標。</span><span class="sxs-lookup"><span data-stu-id="50d72-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="50d72-117">一個或多個資源區塊。</span><span class="sxs-lookup"><span data-stu-id="50d72-117">One or more resource blocks.</span></span> <span data-ttu-id="50d72-118">設定就在這裡為它要設定的資源設定屬性。</span><span class="sxs-lookup"><span data-stu-id="50d72-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="50d72-119">本例有兩個資源區塊，兩個都呼叫 "WindowsFeature" 資源。</span><span class="sxs-lookup"><span data-stu-id="50d72-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="50d72-120">只要可以在 PowerShell 函式中執行的作業，通常在 **[設定]** 區塊內都可以執行。</span><span class="sxs-lookup"><span data-stu-id="50d72-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="50d72-121">例如，在前一個範例中，如果設定的目標電腦名稱不想使用硬式編碼，您可以為節點名稱加入參數：</span><span class="sxs-lookup"><span data-stu-id="50d72-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
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
MyDscConfiguration -ComputerName $ComputerName
```

<span data-ttu-id="50d72-122">在本範例中，您在編譯設定時將節點名稱當作 **ComputerName** 參數來傳遞，藉以指定節點名稱。</span><span class="sxs-lookup"><span data-stu-id="50d72-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="50d72-123">預設名稱為 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="50d72-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="50d72-124">編譯設定</span><span class="sxs-lookup"><span data-stu-id="50d72-124">Compiling the configuration</span></span>

<span data-ttu-id="50d72-125">您必須先將設定編譯成 MOF 文件，才能施行設定。</span><span class="sxs-lookup"><span data-stu-id="50d72-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="50d72-126">呼叫設定即可完成此作業，就像您呼叫 PowerShell 函式一樣。</span><span class="sxs-lookup"><span data-stu-id="50d72-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="50d72-127">範例的最後一行僅包含設定名稱，並會呼叫設定。</span><span class="sxs-lookup"><span data-stu-id="50d72-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="50d72-128">若要呼叫設定，函式必須在全域範圍內 (像任何其他 PowerShell 函式一樣)。</span><span class="sxs-lookup"><span data-stu-id="50d72-128">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="50d72-129">執行此作業的方法有二：「點執行」指令碼，或使用 F5 或按一下 ISE 的 **[執行指令碼]** 按鈕執行設定指令碼。</span><span class="sxs-lookup"><span data-stu-id="50d72-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="50d72-130">若要點執行指令碼，請執行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含設定的指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="50d72-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="50d72-131">當您呼叫設定時，它會：</span><span class="sxs-lookup"><span data-stu-id="50d72-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="50d72-132">解析所有的變數</span><span class="sxs-lookup"><span data-stu-id="50d72-132">Resolves all variables</span></span>
- <span data-ttu-id="50d72-133">在目前的目錄中建立和設定同名的資料夾。</span><span class="sxs-lookup"><span data-stu-id="50d72-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="50d72-134">在新的目錄中建立名為 _NodeName_.mof 的檔案，其中 _NodeName_ 是設定的目標節點名稱。</span><span class="sxs-lookup"><span data-stu-id="50d72-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="50d72-135">如果有多個節點，每個節點都會建立一個 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="50d72-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="50d72-136">MOF 檔案包含目標節點的所有設定資訊。</span><span class="sxs-lookup"><span data-stu-id="50d72-136">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="50d72-137">因為這樣，這個檔案的安全防護很重要。</span><span class="sxs-lookup"><span data-stu-id="50d72-137">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="50d72-138">如需詳細資訊，請參閱[保護 MOF 檔案](secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="50d72-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="50d72-139">編譯上述第一個設定會導致下列的資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="50d72-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="50d72-140">如果設定使用參數，如同第二個範例，則必須在編譯時提供參數。</span><span class="sxs-lookup"><span data-stu-id="50d72-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="50d72-141">它看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="50d72-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="50d72-142">使用 DependsOn</span><span class="sxs-lookup"><span data-stu-id="50d72-142">Using DependsOn</span></span>

<span data-ttu-id="50d72-143">有用的 DSC 關鍵字是 **DependsOn**。</span><span class="sxs-lookup"><span data-stu-id="50d72-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="50d72-144">通常 (但不一定永遠)，DSC 會依設定內的資源出現順序套用資源。</span><span class="sxs-lookup"><span data-stu-id="50d72-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="50d72-145">不過，**DependsOn** 會指定哪一個資源依存於其他資源，而 LCM 則確保它們依正確順序套用，不管資源執行個體的定義順序。</span><span class="sxs-lookup"><span data-stu-id="50d72-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="50d72-146">例如，設定可能會指定 **User** 資源的執行個體依存於 **Group** 執行個體的存在與否：</span><span class="sxs-lookup"><span data-stu-id="50d72-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="50d72-147">在設定中使用新的資源</span><span class="sxs-lookup"><span data-stu-id="50d72-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="50d72-148">如果執行了前面的範例，您可能會注意到，系統警告使用了未明確匯入的資源。</span><span class="sxs-lookup"><span data-stu-id="50d72-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="50d72-149">現在，DSC 在 PSDesiredStateConfiguration 模組中附有 12 種資源。</span><span class="sxs-lookup"><span data-stu-id="50d72-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="50d72-150">外部模組的其他資源必須放置在 `$env:PSModulePath` 中，LCM 才能辨識。</span><span class="sxs-lookup"><span data-stu-id="50d72-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="50d72-151">新的 Cmdlet，[Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)，可用來決定哪些資源要安裝在系統上並提供 LCM 使用。</span><span class="sxs-lookup"><span data-stu-id="50d72-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="50d72-152">這些模組放置在 `$env:PSModulePath` 並由 [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) 正確辨識後，仍需要載入至設定中。</span><span class="sxs-lookup"><span data-stu-id="50d72-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="50d72-153">**Import-DscResource** 是只能在 **Configuration** 區塊中辨識的動態關鍵字 (亦即它不是 Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="50d72-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="50d72-154">**Import-DscResource** 支援兩個參數：</span><span class="sxs-lookup"><span data-stu-id="50d72-154">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="50d72-155">**ModuleName**，使用 **Import-DscResource** 時建議用它。</span><span class="sxs-lookup"><span data-stu-id="50d72-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="50d72-156">它接受包含了要匯入資源 (以及模組名稱字串陣列) 的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="50d72-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="50d72-157">**Name** 是要匯入的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="50d72-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="50d72-158">[Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) 傳回的 "Name" 不是易記的名稱，而是定義資源結構描述時使用的類別名稱 ([Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) 傳回 **ResourceType**)。</span><span class="sxs-lookup"><span data-stu-id="50d72-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="50d72-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50d72-159">See Also</span></span>

- [<span data-ttu-id="50d72-160">Windows PowerShell 預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="50d72-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="50d72-161">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="50d72-161">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="50d72-162">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="50d72-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)