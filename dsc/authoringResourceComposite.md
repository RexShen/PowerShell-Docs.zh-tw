# 複合資源：把 DSC 設定當做資源使用

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

在真實世界的情況裡，設定可能冗長且複雜，要呼叫許多不同的資源，並設定大量的屬性。 為解決這種複雜性，您可以使用 Windows PowerShell 預期狀態設定 (DSC) 設定作為其他設定的資源。 我們稱之為複合資源。 複合資源是使用參數的 DSC 設定。 設定參數的表現如同資源屬性。 設定會儲存為副檔名為 **.schema.psm1** 的檔案，並取代一般 DSC 資源的 MOF 結構描述和資源指令碼 (如需 DSC 資源的詳細資訊，請參閱 [Windows PowerShell 預期狀態設定資源](resources.md)。

## 建立複合資源

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

    # Creae VM specific diff VHD
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

### 將設定儲存為複合資源

若要將參數化設定用作 DSC 資源，請將它儲存在類似任何其他 MOF 型資源的目錄結構中，命名時使用 **.schema.psm1** 副檔名。 本例會將檔案命名為 **xVirtualMachine.schema.psm1**。 您也必須建立名為 **xVirtualMachine.psd1** 的資訊清單，包含下列內容。 請注意，這是除了 **MyDscResources.psd1** 之外，**MyDscResources** 資料夾下所有資源的模組資訊清單。

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

完成之後，資料夾結構應如下。

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSC Resources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

資源現在可使用 Get-DscResource 探索，其屬性也可使用此 Cmdlet 探索，或在 Windows PowerShell ISE 中使用 **Ctrl + 空格鍵**自動完成。

## 使用複合資源

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

## 另請參閱
### 概念
* [撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md)
* [開始使用 Windows PowerShell 預期狀態設定](overview.md)
<!--HONumber=Feb16_HO4-->
