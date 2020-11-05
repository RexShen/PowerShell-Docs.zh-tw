---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 複合資源 - 把 DSC 設定當作資源使用
description: 此文章描述如何建立及使用複合資源。
ms.openlocfilehash: c1f0e3b45c3a393c04700b5a4bc88be365794820
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667295"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="765c4-104">複合資源：把 DSC 設定當做資源使用</span><span class="sxs-lookup"><span data-stu-id="765c4-104">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="765c4-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="765c4-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="765c4-106">在真實世界的情況裡，設定可能冗長且複雜，要呼叫許多不同的資源，並設定大量的屬性。</span><span class="sxs-lookup"><span data-stu-id="765c4-106">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="765c4-107">為解決這種複雜性，您可以使用 Windows PowerShell 預期狀態設定 (DSC) 設定作為其他設定的資源。</span><span class="sxs-lookup"><span data-stu-id="765c4-107">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="765c4-108">這稱為複合資源。</span><span class="sxs-lookup"><span data-stu-id="765c4-108">This is called a composite resource.</span></span> <span data-ttu-id="765c4-109">複合資源是使用參數的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="765c4-109">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="765c4-110">設定參數的表現如同資源屬性。</span><span class="sxs-lookup"><span data-stu-id="765c4-110">The parameters of the configuration act as the properties of the resource.</span></span>
<span data-ttu-id="765c4-111">設定會儲存為副檔名為 `.schema.psm1` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="765c4-111">The configuration is saved as a file with a `.schema.psm1` extension.</span></span> <span data-ttu-id="765c4-112">它會取代 MOF 結構描述和一般 DSC 資源中的資源指令碼。</span><span class="sxs-lookup"><span data-stu-id="765c4-112">It takes the place of both the MOF schema, and the resource script in a typical DSC resource.</span></span> <span data-ttu-id="765c4-113">如需有關 DSC 資源的詳細資訊，請參閱 [Windows PowerShell 預期狀態設定資源](resources.md)。</span><span class="sxs-lookup"><span data-stu-id="765c4-113">For more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="765c4-114">建立複合資源</span><span class="sxs-lookup"><span data-stu-id="765c4-114">Creating the composite resource</span></span>

<span data-ttu-id="765c4-115">在範例中，我們會建立叫用許多現有資源的設定來設定虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="765c4-115">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="765c4-116">不指定要在設定區塊中設定的值，而是讓設定接受之後在設定區塊中使用的參數。</span><span class="sxs-lookup"><span data-stu-id="765c4-116">Instead of specifying the values to be set in configuration blocks, the configuration takes in parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="765c4-117">DSC 目前不支援將複合資源或巢狀設定放在複合資源內。</span><span class="sxs-lookup"><span data-stu-id="765c4-117">DSC doesn't currently support placing composite resources or nested configurations within a composite resource.</span></span>

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="765c4-118">將設定儲存為複合資源</span><span class="sxs-lookup"><span data-stu-id="765c4-118">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="765c4-119">若要使用參數化設定作為 DSC 資源，請將它儲存在類似任何其他 MOF 型資源之目錄結構的目錄結構中，然後以 `.schema.psm1` 附檔名為其命名。</span><span class="sxs-lookup"><span data-stu-id="765c4-119">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a `.schema.psm1` extension.</span></span> <span data-ttu-id="765c4-120">針對此範例，我們會將檔案命名為 `xVirtualMachine.schema.psm1`。</span><span class="sxs-lookup"><span data-stu-id="765c4-120">For this example, we'll name the file `xVirtualMachine.schema.psm1`.</span></span> <span data-ttu-id="765c4-121">您還必須建立名為 `xVirtualMachine.psd1` 且包含下列行的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="765c4-121">You also need to create a manifest named `xVirtualMachine.psd1` that contains the following line.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

> [!NOTE]
> <span data-ttu-id="765c4-122">這是 `MyDscResources.psd1` (`MyDscResources` 資料夾底下所有資源的模組資訊清單) 以外的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="765c4-122">This is in addition to `MyDscResources.psd1`, the module manifest for all resources under the `MyDscResources` folder.</span></span>

<span data-ttu-id="765c4-123">完成之後，資料夾結構應如下。</span><span class="sxs-lookup"><span data-stu-id="765c4-123">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
        |- MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="765c4-124">現在可使用 `Get-DscResource` Cmdlet 來探索資源，也可使用該 Cmdlet 或在 Windows PowerShell ISE 中使用 <kbd>Ctrl</kbd>+<kbd>空格鍵</kbd>自動完成來探索其屬性。</span><span class="sxs-lookup"><span data-stu-id="765c4-124">The resource is now discoverable by using the `Get-DscResource` cmdlet, and its properties are discoverable by either that cmdlet or by using <kbd>Ctrl</kbd>+<kbd>Space</kbd> autocomplete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="765c4-125">使用複合資源</span><span class="sxs-lookup"><span data-stu-id="765c4-125">Using the composite resource</span></span>

<span data-ttu-id="765c4-126">接下來我們要建立呼叫複合資源的設定。</span><span class="sxs-lookup"><span data-stu-id="765c4-126">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="765c4-127">這個設定會呼叫 xVirtualMachine 複合資源，以建立虛擬機器，然後再呼叫 **xComputer** 資源重新命名它。</span><span class="sxs-lookup"><span data-stu-id="765c4-127">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell
configuration RenameVM
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

<span data-ttu-id="765c4-128">您也可以使用此資源來建立多部 VM，只要將 VM 名稱的陣列傳遞給 xVirtualMachine 資源即可。</span><span class="sxs-lookup"><span data-stu-id="765c4-128">You can also use this resource to create multiple VMs by passing in an array of VM names to the xVirtualMachine resource.</span></span>

```PowerShell
Configuration MultipleVms
{
    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VMs
        {
            VMName = "IIS01", "SQL01", "SQL02"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="765c4-129">支援 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="765c4-129">Supporting PsDscRunAsCredential</span></span>

> [!NOTE]
> <span data-ttu-id="765c4-130">PowerShell 5.0 或更新版本中支援 **PsDscRunAsCredential** 。</span><span class="sxs-lookup"><span data-stu-id="765c4-130">**PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="765c4-131">您可以在 [DSC 設定](../configurations/configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="765c4-131">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="765c4-132">如需詳細資訊，請參閱[以使用者認證執行 DSC](../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="765c4-132">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="765c4-133">若要從自訂資源內存取使用者內容，您可以使用自動變數 `$PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="765c4-133">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="765c4-134">例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：</span><span class="sxs-lookup"><span data-stu-id="765c4-134">For example, the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="765c4-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="765c4-135">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="765c4-136">概念</span><span class="sxs-lookup"><span data-stu-id="765c4-136">Concepts</span></span>

- [<span data-ttu-id="765c4-137">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="765c4-137">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="765c4-138">開始使用 Windows PowerShell 預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="765c4-138">Get Started with Windows PowerShell Desired State Configuration</span></span>](../overview/overview.md)
