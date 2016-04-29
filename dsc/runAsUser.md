# 以使用者認證執行 DSC 

> 適用於：Windows PowerShell 5.0

您可以在設定中使用 **PsDscRunAsCredential** 屬性，以一組指定的認證來執行 DSC 設定。 根據預設，DSC 會
以系統帳戶身分執行。 在某些情況下，您必須以使用者身分執行，例如在特定使用者內容中安裝 MSI 套件、設定使用者的登錄機碼、
存取使用者的特定本機目錄，或存取網路共用。

每個 DSC 資源都有 **PsDscRunAsCredential** 屬性，可設為任何使用者認證 ([PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) 物件)。
認證可經硬式編碼成為設定中的屬性值，您也可以將此值設為 [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx)，
這會在編譯設定時，提示使用者輸入認證 (如需編譯設定的資訊，請參閱[設定](configurations.md))。

>**注意**：**PsDscRunAsCredential** 屬性不適用於 PowerShell 4.0。

在下列範例中，使用了 **Get-Credential** 來提示使用者輸入認證。 [Registry](registryResource.md) 資源可用來變更指定
Windows 命令提示字元視窗背景色彩的登錄機碼。

```powershell
Configuration ChangeCmdBackGroundColor    

{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName

    {
        Registry CmdPath

        {

            Key = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = Get-Credential
        }
    }                   
}

$configData = @{

    AllNodes = @(

    @{

        NodeName="localhost";
        PSDscAllowDomainUser = $true
        CertificateFile = "C:\publicKeys\targetNode.cer"
        Thumbprint = "7ee7f09d-4be0-41aa-a47f-96b9e3bdec25"

    })

}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**注意**︰這個範例假設您在 `C:\publicKeys\targetNode.cer` 中具有有效的憑證，而且該憑證的指紋是所顯示的值。
>如需在 DSC 設定 MOF 檔案中加密認證的資訊，請參閱[保護 MOF 檔案](secureMOF.md)。 



<!--HONumber=Mar16_HO2-->


