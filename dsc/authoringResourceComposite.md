---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "複合資源：把 DSC 設定當做資源使用"
ms.openlocfilehash: 1d5fb89eb9845820de8543f388ddb6aaeaaa3e44
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a>複合資源：把 DSC 設定當做資源使用

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

在真實世界的情況裡，設定可能冗長且複雜，要呼叫許多不同的資源，並設定大量的屬性。 為解決這種複雜性，您可以使用 Windows PowerShell 預期狀態設定 (DSC) 設定作為其他設定的資源。 我們稱之為複合資源。 複合資源是使用參數的 DSC 設定。 設定參數的表現如同資源屬性。 設定會儲存為副檔名為 **.schema.psm1** 的檔案，並取代一般 DSC 資源的 MOF 結構描述和資源指令碼 (如需 DSC 資源的詳細資訊，請參閱 [Windows PowerShell 預期狀態設定資源](resources.md)。

## <a name="creating-the-composite-resource"></a>建立複合資源

在範例中，我們會建立叫用許多現有資源的設定來設定虛擬機器。 不指定要在設定區塊中設定的值，而是讓設定使用之後要用在設定區塊中的許多參數。

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

### <a name="saving-the-configuration-as-a-composite-resource"></a>將設定儲存為複合資源

若要將參數化設定用作 DSC 資源，請將它儲存在類似任何其他 MOF 型資源的目錄結構中，命名時使用 **.schema.psm1** 副檔名。 本例會將檔案命名為 **xVirtualMachine.schema.psm1**。 您也必須建立名為 **xVirtualMachine.psd1** 的資訊清單，包含下列內容。 請注意，這是除了 **MyDscResources.psd1** 之外，**MyDscResources** 資料夾下所有資源的模組資訊清單。

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

完成之後，資料夾結構應如下。

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

資源現在可使用 Get-DscResource 探索，其屬性也可使用此 Cmdlet 探索，或在 Windows PowerShell ISE 中使用 **Ctrl + 空格鍵**自動完成。

## <a name="using-the-composite-resource"></a>使用複合資源

接下來我們要建立呼叫複合資源的設定。 這個設定會呼叫 xVirtualMachine 複合資源，以建立虛擬機器，然後再呼叫 **xComputer** 資源重新命名它。

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

## <a name="supporting-psdscrunascredential"></a>支援 PsDscRunAsCredential

>**注意：**支援 **PsDscRunAsCredential** 的是 PowerShell 5.0 和更新版本。

您可以在 [DSC 設定](configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。
如需詳細資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。

若要從自訂資源內存取使用者內容，您可以使用自動變數 `$PsDscContext`。

例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a>另請參閱
### <a name="concepts"></a>概念
* [撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md)
* [開始使用 Windows PowerShell 預期狀態設定](overview.md)

