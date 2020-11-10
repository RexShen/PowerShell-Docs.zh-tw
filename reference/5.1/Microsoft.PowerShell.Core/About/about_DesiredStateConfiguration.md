---
description: 提供 PowerShell Desired State Configuration (DSC) 功能的簡介。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 5d088934ffc953ad19be401bce72f6287f0fde07
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387017"
---
# <a name="about_desiredstateconfiguration"></a><span data-ttu-id="d2d1e-104">about_DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2d1e-104">about_DesiredStateConfiguration</span></span>

## <a name="short-description"></a><span data-ttu-id="d2d1e-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d2d1e-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d2d1e-106">提供 PowerShell Desired State Configuration (DSC) 功能的簡介。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-106">Provides a brief introduction to the PowerShell Desired State Configuration (DSC) feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="d2d1e-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="d2d1e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d2d1e-108">DSC 是 PowerShell 中的管理平臺，可讓您部署和管理軟體服務的設定資料，以及管理這些服務執行所在的環境。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-108">DSC is a management platform in PowerShell that enables deploying and managing configuration data for software services, and managing the environment in which these services run.</span></span>

<span data-ttu-id="d2d1e-109">DSC 提供一組 PowerShell 語言擴充功能、新的 Cmdlet 和資源，您可以用來以宣告方式指定要如何設定軟體環境的狀態。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-109">DSC provides a set of PowerShell language extensions, new cmdlets, and resources that you can use to declaratively specify how you want the state of your software environment to be configured.</span></span> <span data-ttu-id="d2d1e-110">它也提供方法來維護和管理現有的設定。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-110">It also provides a means to maintain and manage existing configurations.</span></span>

<span data-ttu-id="d2d1e-111">DSC 是在 PowerShell 4.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-111">DSC is introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="d2d1e-112">如需 DSC 的詳細資訊，請參閱 [PowerShell Desired State Configuration 總覽](/powershell/scripting/dsc/overview/overview)。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-112">For detailed information about DSC, see [PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview).</span></span>

## <a name="developing-dsc-resources-with-classes"></a><span data-ttu-id="d2d1e-113">使用類別開發 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d2d1e-113">DEVELOPING DSC RESOURCES WITH CLASSES</span></span>

<span data-ttu-id="d2d1e-114">從 PowerShell 5.0 開始，您可以使用類別來開發 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-114">Starting in PowerShell 5.0, you can develop DSC resources by using classes.</span></span>
<span data-ttu-id="d2d1e-115">如需詳細資訊，請參閱 [about_Classes](about_Classes.md)，以及 [使用 PowerShell 類別撰寫自訂 DSC 資源](/powershell/scripting/dsc/resources/authoringresourceclass)。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-115">For more information, see [about_Classes](about_Classes.md), and [Writing a custom DSC resource with PowerShell classes](/powershell/scripting/dsc/resources/authoringresourceclass).</span></span>

## <a name="using-dsc"></a><span data-ttu-id="d2d1e-116">使用 DSC</span><span class="sxs-lookup"><span data-stu-id="d2d1e-116">USING DSC</span></span>

<span data-ttu-id="d2d1e-117">若要使用 DSC 來設定您的環境，請先使用設定關鍵字來定義 PowerShell 腳本區塊，後面接著識別碼，後面接著成對的大括弧來分隔區塊。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-117">To use DSC to configure your environment, first define a PowerShell script block using the Configuration keyword, followed by an identifier, which is in turn followed by the pair of curly braces delimiting the block.</span></span> <span data-ttu-id="d2d1e-118">在設定區塊內，您可以定義節點區塊，以指定環境中 (電腦) 的每個節點所需的設定狀態。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-118">Inside the configuration block you can define node blocks that specify the desired configuration state for each node (computer) in the environment.</span></span> <span data-ttu-id="d2d1e-119">節點區塊會以 Node 關鍵字開頭，後面接著目的電腦的名稱（可以是變數）。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-119">A node block starts with the Node keyword, followed by the name of the target computer, which can be a variable.</span></span> <span data-ttu-id="d2d1e-120">在電腦名稱稱之後，以大括弧分隔節點區塊。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-120">After the computer name, come the curly braces that delimit the node block.</span></span> <span data-ttu-id="d2d1e-121">在節點區塊內，您可以定義用來設定特定資源的資源區塊。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-121">Inside the node block, you can define resource blocks to configure specific resources.</span></span> <span data-ttu-id="d2d1e-122">資源區塊會以資源的類型名稱為開頭，後面接著您想要為該區塊指定的識別碼，後面接著用來分隔區塊的大括弧，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-122">A resource block starts with the type name of the resource, followed by the identifier you want to specify for that block, followed by the curly braces that delimit the block, as shown in the following example.</span></span>

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

<span data-ttu-id="d2d1e-123">若要建立設定，請以您叫用 PowerShell 函式的相同方式叫用設定區塊，傳遞您可能已在上述範例中定義 (兩個參數的任何預期參數) 。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-123">To create a configuration, invoke the Configuration block the same way you would invoke a PowerShell function, passing in any expected parameters you may have defined (two in the example above).</span></span> <span data-ttu-id="d2d1e-124">例如，在此情況下：</span><span class="sxs-lookup"><span data-stu-id="d2d1e-124">For example, in this case:</span></span>

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

<span data-ttu-id="d2d1e-125">這會在您指定的路徑上每個節點產生一個 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-125">This generates a MOF file per node at the path you specify.</span></span> <span data-ttu-id="d2d1e-126">這些 MOF 檔案會指定每個節點所需的設定。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-126">These MOF files specify the desired configuration for each node.</span></span> <span data-ttu-id="d2d1e-127">接下來，使用下列 Cmdlet 來剖析設定 MOF 檔案、將每個節點傳送到其對應的設定，並制定這些設定。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-127">Next, use the following cmdlet to parse the configuration MOF files, send each node its corresponding configuration, and enact those configurations.</span></span> <span data-ttu-id="d2d1e-128">請注意，您不需要為以類別為基礎的 DSC 資源建立個別的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-128">Note that you do not need to create a separate MOF file for class-based DSC resources.</span></span>

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a><span data-ttu-id="d2d1e-129">使用 DSC 維護設定狀態</span><span class="sxs-lookup"><span data-stu-id="d2d1e-129">USING DSC TO MAINTAIN CONFIGURATION STATE</span></span>

<span data-ttu-id="d2d1e-130">使用 DSC 時，設定為等冪。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-130">With DSC, configuration is idempotent.</span></span> <span data-ttu-id="d2d1e-131">這表示，如果您使用 DSC 來進行相同的設定，則產生的設定狀態一律會相同。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-131">This means that if you use DSC to enact the same configuration more than once, the resulting configuration state will always be the same.</span></span> <span data-ttu-id="d2d1e-132">基於這個原因，如果您懷疑環境中的任何節點可能已從所需的設定狀態漂移，您可以再次制定相同的 DSC 設定，使其回到預期的狀態。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-132">Because of this, if you suspect that any nodes in your environment may have drifted from the desired state of configuration, you can enact the same DSC configuration again to bring them back to the desired state.</span></span> <span data-ttu-id="d2d1e-133">您不需要修改設定腳本來處理其狀態已從所需狀態漂移的資源。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-133">You do not need to modify the configuration script to address only those resources whose state has drifted from the desired state.</span></span>

<span data-ttu-id="d2d1e-134">下列範例示範如何確認指定節點上設定的實際狀態是否已從節點上的最後一個 DSC 設定漂移。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-134">The following example shows how you can verify whether the actual state of configuration on a given node has drifted from the last DSC configuration enacted on the node.</span></span> <span data-ttu-id="d2d1e-135">在此範例中，我們會檢查本機電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-135">In this example we are checking the configuration of the local computer.</span></span>

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a><span data-ttu-id="d2d1e-136">內建 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d2d1e-136">BUILT-IN DSC RESOURCES</span></span>

<span data-ttu-id="d2d1e-137">您可以在設定腳本中使用下列內建資源：</span><span class="sxs-lookup"><span data-stu-id="d2d1e-137">You can use the following built-in resources in your configuration scripts:</span></span>

|<span data-ttu-id="d2d1e-138">名稱</span><span class="sxs-lookup"><span data-stu-id="d2d1e-138">Name</span></span>                  |<span data-ttu-id="d2d1e-139">屬性</span><span class="sxs-lookup"><span data-stu-id="d2d1e-139">Properties</span></span>                                         |
|----------------------|---------------------------------------------------|
|<span data-ttu-id="d2d1e-140">檔案</span><span class="sxs-lookup"><span data-stu-id="d2d1e-140">File</span></span>                  |<span data-ttu-id="d2d1e-141">{DestinationPath，屬性，總和檢查碼，內容 ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-141">{DestinationPath, Attributes, Checksum, Content...}</span></span>|
|<span data-ttu-id="d2d1e-142">封存</span><span class="sxs-lookup"><span data-stu-id="d2d1e-142">Archive</span></span>               |<span data-ttu-id="d2d1e-143">{Destination、Path、Checksum、Credential ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-143">{Destination, Path, Checksum, Credential...}</span></span>       |
|<span data-ttu-id="d2d1e-144">環境</span><span class="sxs-lookup"><span data-stu-id="d2d1e-144">Environment</span></span>           |<span data-ttu-id="d2d1e-145">{Name，DependsOn，確定，Path ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-145">{Name, DependsOn, Ensure, Path...}</span></span>                 |
|<span data-ttu-id="d2d1e-146">群組</span><span class="sxs-lookup"><span data-stu-id="d2d1e-146">Group</span></span>                 |<span data-ttu-id="d2d1e-147">{身分、Credential、DependsOn、Description ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-147">{GroupName, Credential, DependsOn, Description...}</span></span> |
|<span data-ttu-id="d2d1e-148">記錄</span><span class="sxs-lookup"><span data-stu-id="d2d1e-148">Log</span></span>                   |<span data-ttu-id="d2d1e-149">{Message，DependsOn，PsDscRunAsCredential}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-149">{Message, DependsOn, PsDscRunAsCredential}</span></span>         |
|<span data-ttu-id="d2d1e-150">套件</span><span class="sxs-lookup"><span data-stu-id="d2d1e-150">Package</span></span>               |<span data-ttu-id="d2d1e-151">{Name、Path、ProductId、Arguments ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-151">{Name, Path, ProductId, Arguments...}</span></span>              |
|<span data-ttu-id="d2d1e-152">登錄</span><span class="sxs-lookup"><span data-stu-id="d2d1e-152">Registry</span></span>              |<span data-ttu-id="d2d1e-153">{Key，ValueName，DependsOn，確定 ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-153">{Key, ValueName, DependsOn, Ensure...}</span></span>             |
|<span data-ttu-id="d2d1e-154">指令碼</span><span class="sxs-lookup"><span data-stu-id="d2d1e-154">Script</span></span>                |<span data-ttu-id="d2d1e-155">{>getscript，SetScript，>testscript，Credential ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-155">{GetScript, SetScript, TestScript, Credential...}</span></span>  |
|<span data-ttu-id="d2d1e-156">服務</span><span class="sxs-lookup"><span data-stu-id="d2d1e-156">Service</span></span>               |<span data-ttu-id="d2d1e-157">{Name，>builtinaccount，Credential，相依性 ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-157">{Name, BuiltInAccount, Credential, Dependencies...}</span></span>|
|<span data-ttu-id="d2d1e-158">User</span><span class="sxs-lookup"><span data-stu-id="d2d1e-158">User</span></span>                  |<span data-ttu-id="d2d1e-159">{UserName，DependsOn，Description，Disabled ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-159">{UserName, DependsOn, Description, Disabled...}</span></span>    |
|<span data-ttu-id="d2d1e-160">WaitForAll</span><span class="sxs-lookup"><span data-stu-id="d2d1e-160">WaitForAll</span></span>            |<span data-ttu-id="d2d1e-161">{NodeName，CoNtext.resourcename，DependsOn，PsDscRunAsC ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-161">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="d2d1e-162">WaitForAny</span><span class="sxs-lookup"><span data-stu-id="d2d1e-162">WaitForAny</span></span>            |<span data-ttu-id="d2d1e-163">{NodeName，CoNtext.resourcename，DependsOn，PsDscRunAsC ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-163">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="d2d1e-164">WaitForSome</span><span class="sxs-lookup"><span data-stu-id="d2d1e-164">WaitForSome</span></span>           |<span data-ttu-id="d2d1e-165">{NodeCount，NodeName，CoNtext.resourcename，DependsOn ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-165">{NodeCount, NodeName, ResourceName, DependsOn...}</span></span>  |
|<span data-ttu-id="d2d1e-166">WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="d2d1e-166">WindowsFeature</span></span>        |<span data-ttu-id="d2d1e-167">{Name，Credential，DependsOn，確定 ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-167">{Name, Credential, DependsOn, Ensure...}</span></span>           |
|<span data-ttu-id="d2d1e-168">WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="d2d1e-168">WindowsOptionalFeature</span></span>|<span data-ttu-id="d2d1e-169">{Name，DependsOn，確定，LogLevel ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-169">{Name, DependsOn, Ensure, LogLevel...}</span></span>             |
|<span data-ttu-id="d2d1e-170">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="d2d1e-170">WindowsProcess</span></span>        |<span data-ttu-id="d2d1e-171">{Arguments，Path，Credential，DependsOn ...}</span><span class="sxs-lookup"><span data-stu-id="d2d1e-171">{Arguments, Path, Credential, DependsOn...}</span></span>        |

<span data-ttu-id="d2d1e-172">若要取得您系統上可用的 DSC 資源清單，請執行 `Get-DscResource` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-172">To get a list of available DSC resources on your system, run the `Get-DscResource` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d2d1e-173">在 7.0 版以前的 PowerShell 中，`Get-DscResource` 不會尋找類別型的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-173">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="d2d1e-174">本主題中的範例將示範如何使用 File 和的資源。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-174">The example in this topic demonstrates how to use the File and WindowsFeature resources.</span></span> <span data-ttu-id="d2d1e-175">若要查看您可以搭配資源使用的所有屬性，請在資源關鍵字中插入游標 (例如，在 PowerShell ISE 的設定腳本內的檔案) ，按住<kbd>CTRL</kbd> + <kbd>空格鍵</kbd></span><span class="sxs-lookup"><span data-stu-id="d2d1e-175">To see all properties that you can use with a resource, insert the cursor in the resource keyword (for example, File) within your configuration script in PowerShell ISE, hold down <kbd>CTRL</kbd>+<kbd>SPACEBAR</kbd></span></span>

## <a name="find-more-resources"></a><span data-ttu-id="d2d1e-176">尋找更多資源</span><span class="sxs-lookup"><span data-stu-id="d2d1e-176">FIND MORE RESOURCES</span></span>

<span data-ttu-id="d2d1e-177">您可以下載、安裝及瞭解 PowerShell 和 DSC 使用者群體和 Microsoft 所建立的許多其他可用的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-177">You can download, install, and learn about many other available DSC resources that have been created by the PowerShell and DSC user community, and by Microsoft.</span></span> <span data-ttu-id="d2d1e-178">請流覽 [PowerShell 資源庫](https://www.powershellgallery.com/) ，以流覽及瞭解可用的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d2d1e-178">Visit the [PowerShell Gallery](https://www.powershellgallery.com/) to browse and learn about available DSC resources.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2d1e-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2d1e-179">SEE ALSO</span></span>

[<span data-ttu-id="d2d1e-180">PowerShell Desired State Configuration 總覽</span><span class="sxs-lookup"><span data-stu-id="d2d1e-180">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="d2d1e-181">內建 PowerShell Desired State Configuration 資源</span><span class="sxs-lookup"><span data-stu-id="d2d1e-181">Built-In PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/resources)

[<span data-ttu-id="d2d1e-182">建立自訂的 PowerShell Desired State Configuration 資源</span><span class="sxs-lookup"><span data-stu-id="d2d1e-182">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
