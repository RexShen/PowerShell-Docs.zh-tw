---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "複合資源：把 DSC 設定當做資源使用"
ms.openlocfilehash: d889384c8d9c0746200ad424c6ab448a0e41d66c
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="17327-103">複合資源：把 DSC 設定當做資源使用</span><span class="sxs-lookup"><span data-stu-id="17327-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="17327-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="17327-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="17327-105">在真實世界的情況裡，設定可能冗長且複雜，要呼叫許多不同的資源，並設定大量的屬性。</span><span class="sxs-lookup"><span data-stu-id="17327-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="17327-106">為解決這種複雜性，您可以使用 Windows PowerShell 預期狀態設定 (DSC) 設定作為其他設定的資源。</span><span class="sxs-lookup"><span data-stu-id="17327-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="17327-107">我們稱之為複合資源。</span><span class="sxs-lookup"><span data-stu-id="17327-107">We call this a composite resource.</span></span> <span data-ttu-id="17327-108">複合資源是使用參數的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="17327-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="17327-109">設定參數的表現如同資源屬性。</span><span class="sxs-lookup"><span data-stu-id="17327-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="17327-110">設定會儲存為副檔名為 **.schema.psm1** 的檔案，並取代一般 DSC 資源的 MOF 結構描述和資源指令碼 (如需 DSC 資源的詳細資訊，請參閱 [Windows PowerShell 預期狀態設定資源](resources.md)。</span><span class="sxs-lookup"><span data-stu-id="17327-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="17327-111">建立複合資源</span><span class="sxs-lookup"><span data-stu-id="17327-111">Creating the composite resource</span></span>

<span data-ttu-id="17327-112">在範例中，我們會建立叫用許多現有資源的設定來設定虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="17327-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="17327-113">不指定要在設定區塊中設定的值，而是讓設定使用之後要用在設定區塊中的許多參數。</span><span class="sxs-lookup"><span data-stu-id="17327-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

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

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="17327-114">將設定儲存為複合資源</span><span class="sxs-lookup"><span data-stu-id="17327-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="17327-115">若要將參數化設定用作 DSC 資源，請將它儲存在類似任何其他 MOF 型資源的目錄結構中，命名時使用 **.schema.psm1** 副檔名。</span><span class="sxs-lookup"><span data-stu-id="17327-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="17327-116">本例會將檔案命名為 **xVirtualMachine.schema.psm1**。</span><span class="sxs-lookup"><span data-stu-id="17327-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="17327-117">您也必須建立名為 **xVirtualMachine.psd1** 的資訊清單，包含下列內容。</span><span class="sxs-lookup"><span data-stu-id="17327-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="17327-118">請注意，這是除了 **MyDscResources.psd1** 之外，**MyDscResources** 資料夾下所有資源的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="17327-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="17327-119">完成之後，資料夾結構應如下。</span><span class="sxs-lookup"><span data-stu-id="17327-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="17327-120">資源現在可使用 Get-DscResource 探索，其屬性也可使用此 Cmdlet 探索，或在 Windows PowerShell ISE 中使用 **Ctrl + 空格鍵**自動完成。</span><span class="sxs-lookup"><span data-stu-id="17327-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="17327-121">使用複合資源</span><span class="sxs-lookup"><span data-stu-id="17327-121">Using the composite resource</span></span>

<span data-ttu-id="17327-122">接下來我們要建立呼叫複合資源的設定。</span><span class="sxs-lookup"><span data-stu-id="17327-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="17327-123">這個設定會呼叫 xVirtualMachine 複合資源，以建立虛擬機器，然後再呼叫 **xComputer** 資源重新命名它。</span><span class="sxs-lookup"><span data-stu-id="17327-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell

configuration RenameVM
{

    Import-DscResource -Module TestCompositeResource
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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="17327-124">支援 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="17327-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="17327-125">**注意：**支援 **PsDscRunAsCredential** 的是 PowerShell 5.0 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="17327-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="17327-126">您可以在 [DSC 設定](configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="17327-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="17327-127">如需詳細資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="17327-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="17327-128">若要從自訂資源內存取使用者內容，您可以使用自動變數 `$PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="17327-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="17327-129">例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：</span><span class="sxs-lookup"><span data-stu-id="17327-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="17327-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17327-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="17327-131">概念</span><span class="sxs-lookup"><span data-stu-id="17327-131">Concepts</span></span>
* [<span data-ttu-id="17327-132">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="17327-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="17327-133">開始使用 Windows PowerShell 預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="17327-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)

