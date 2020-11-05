---
ms.date: 07/06/2020
keywords: dsc,powershell,設定,安裝
title: 保護 MOF 檔案
description: 此文章描述如何確保目標節點已將 MOF 檔案加密。
ms.openlocfilehash: e8b495a5c3c18dca5cde29cbbcf7d3f3cdab8f48
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662802"
---
# <a name="securing-the-mof-file"></a>保護 MOF 檔案

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

DSC 會藉由套用儲存在 MOF 檔案中的資訊來管理伺服器節點的設定，而 MOF 檔案是本機系統管理員 (LCM) 實作所需結束狀態的位置。 因為這個檔案包含設定的詳細資料，所以安全防護很重要。 此文章描述如何確保目標節點已將檔案加密。

從 PowerShell 5.0 版開始，使用 `Start-DSCConfiguration` Cmdlet 將 MOF 檔案套用到節點時，預設會加密整個 MOF 檔案。 當憑證未受管理，使用提取服務通訊協定來實作解決方案時，才需要文中所述的程序來確保目標節點所下載的設定在套用前能夠讓系統解密和讀取 (例如，Windows Server 提供的提取服務)。 向 [Azure 自動化 DSC](/azure/automation/automation-dsc-overview) 註冊的節點會自動安裝憑證，並交由服務管理而不需任何管理費用。

> [!NOTE]
> 本主題討論用於加密的憑證。 以自我簽署憑證進行加密便已足夠，因為私密金鑰一律會受到保護，且加密不代表信任文件。 自我簽署憑證 _不能_ 用來進行驗證。 您應該使用來自信任憑證授權單位 (CA) 的憑證進行任何驗證。

## <a name="prerequisites"></a>Prerequisites

若要成功地加密用來保護 DSC 設定的認證，請確定您具備下列項目：

- **發行與散發憑證的一些方法** 。 本主題和範例假設您使用的是 Active Directory 憑證授權單位。 如需有關 Active Directory 憑證服務的詳細資訊，請參閱 [Active Directory 憑證服務概觀](https://technet.microsoft.com/library/hh831740.aspx)和 [Windows Server 2008 的 Active Directory 憑證服務](https://technet.microsoft.com/windowsserver/dd448615.aspx)。
- **目標節點或節點的系統管理存取權** 。
- **每個目標節點在其個人存放區都儲存了支援加密的憑證** 。 在 Windows PowerShell 中，存放區的路徑是 Cert:\LocalMachine\My。 本主題中的範例會使用「工作站驗證」範本，您可在[預設憑證範本](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx)中找到它和其他憑證範本。
- 如果在目標節點以外的電腦上執行這項設定，請 **匯出憑證的公開金鑰** ，將它匯入要執行設定的電腦。 確定只匯出 **公用** 金鑰，妥善保管私密金鑰。

> [!NOTE]
> 指令碼資源具有一些加密限制。 如需詳細資訊，請參閱[指令碼資源](../reference/resources/windows/scriptResource.md#known-limitations)

## <a name="overall-process"></a>整體程序

 1. 設定憑證、金鑰和指紋，並確定每個目標節點都有憑證複本，而設定電腦則有公開金鑰和指紋。
 1. 建立包含公開金鑰路徑和指紋的設定資料區塊。
 1. 建立為目標節點定義所需設定的設定指令碼，以及指揮本機設定管理員使用憑證及其指紋解密設定資料，設定目標節點的解密。
 1. 執行設定，會設定本機設定管理員的設定並啟動 DSC 設定。

![認證加密的程序流程](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>憑證需求

若要制定認證加密，用來撰寫 DSC 設定之電腦所 **信任** 的 _目標節點_ 上必須有公開金鑰憑證可用。 此公開金鑰憑證具有可讓其用於 DSC 認證加密的特定需求︰

1. **金鑰使用方法** ：
   - 必須包含：'KeyEncipherment' 和 'DataEncipherment'。
   - 「不得」包含：「數位簽章」。
1. **增強金鑰使用方法** ：
   - 必須包含：文件加密 (1.3.6.1.4.1.311.80.1)。
   - 「不得」包含：用戶端驗證 (1.3.6.1.5.5.7.3.2) 與伺服器驗證 (1.3.6.1.5.5.7.3.1)。
1. *Target Node_ 上有憑證的私密金鑰可用。
1. 憑證的 **提供者** 必須是「Microsoft RSA SChannel 密碼編譯提供者」。

> [!IMPORTANT]
> 雖然可使用的憑證，其含有「數位簽章」的金鑰使用方法，或驗證 EKU 的其中一個憑證，但這將導致加密金鑰更容易被誤用且很容易遭受攻擊。 因此，最佳做法是使用專為保護 DSC 認證所建立的憑證，來省略這些金鑰使用方法和 EKU。

您可以在 _目標節點_ 上，使用符合這些準則的任何現有憑證來保護 DSC 認證。

## <a name="certificate-creation"></a>建立憑證

建立及使用必要的加密憑證 (成對的公用/私密金鑰組) 有兩種方法。

1. 在 **目標節點** 上建立，並只將公用金鑰匯出至 **撰寫節點**
1. 在 **撰寫節點** 上建立，並將整組成對的金鑰匯出至 **目標節點**

因為用於在 MOF 中解密認證的私密金鑰，會一直保存在目標節點中，所建議採用方法 1。

### <a name="creating-the-certificate-on-the-target-node"></a>在目標節點上建立憑證

由於會使用私密金鑰在 **目標節點** 上將 MOF 解密，因此請務必確保其安全。最簡單的方法是在 **目標節點** 上建立私密金鑰憑證，並將 **公開金鑰憑證** 複製到用於將 DSC 設定撰寫入 MOF 檔案的電腦。 下列範例將：

1. 在 **目標節點** 上建立憑證
1. 在 **目標節點** 上匯出公開金鑰憑證。
1. 在 **撰寫節點** 上將公開金鑰憑證匯入 **我的** 憑證存放區。

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>在目標節點上︰ 建立及匯出憑證

> 目標節點：Windows Server 2016 與 Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

匯出之後，必須將 `DscPublicKey.cer` 複製到 **撰寫節點** 。

> 目標節點：Windows Server 2012 R2/Windows 8.1 及更早版本

> [!WARNING]
> 因為在比 Windows 10 和 Windows Server 2016 更早的 Windows 作業系統上，`New-SelfSignedCertificate` Cmdlet 不支援 **Type** 參數，所以在這些作業系統上需要建立此憑證的替代方法。 在此情況下，可以使用 `makecert.exe` 或 `certutil.exe` 來建立憑證。 替代方法是從 Microsoft 指令碼中心下載 [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) \(英文\) 指令碼，並改為加以使用來建立憑證︰

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

匯出之後，必須將 ```DscPublicKey.cer``` 複製到 **撰寫節點** 。

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>在撰寫節點上︰匯入憑證的公開金鑰

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>在撰寫節點上建立憑證

或者，在 **撰寫節點** 上建立加密憑證，搭配 **私密金鑰** 作為 PFX 檔案進行匯出，然後再匯入到 **目標節點** 上。 這是目前在 _Nano Server_ 上實作 DSC 認證加密的方法。 雖然有使用密碼保護 PFX，在傳輸期間也應該保持安全狀態。 下列範例將：

1. 在 **撰寫節點** 上建立憑證。
1. 在 **撰寫節點** 上匯出包含私密金鑰的憑證。
1. 從 **製作節點** 移除私密金鑰 ，但保留 **我的** 存放區中之公開金鑰憑證。
1. 將私密金鑰憑證匯入 **目標節點** 上我的 (個人) 憑證存放區。
   - 它必須加入根存放區，才會得到 **目標節點** 的信任。

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>在撰寫節點上：建立及匯出憑證

> 目標節點：Windows Server 2016 與 Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

匯出之後，必須將 `DscPrivateKey.pfx` 複製到 **目標節點** 。

> 目標節點：Windows Server 2012 R2/Windows 8.1 及更早版本

> [!WARNING]
> 因為在比 Windows 10 和 Windows Server 2016 更早的 Windows 作業系統上，`New-SelfSignedCertificate` Cmdlet 不支援 **Type** 參數，所以在這些作業系統上需要建立此憑證的替代方法。 在此情況下，可以使用 `makecert.exe` 或 `certutil.exe` 來建立憑證。 替代方法是從 Microsoft 指令碼中心下載 [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) \(英文\) 指令碼，並改為加以使用來建立憑證︰

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>在目標節點上︰匯入憑證的私密金鑰作為受信任的根

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>設定資料

設定資料區塊會定義哪些是執行作業的目標節點、是否加密認證、加密方法和其他資訊。 如需設定資料區塊的詳細資訊，請參閱[分離設定和環境資料](../configurations/configData.md)。

可為每個認證加密相關節點進行設定的項目包括：

- **NodeName** - 要設定認證加密的目標節點名稱。
- **PsDscAllowPlainTextPassword** - 是否允許將未加密的認證傳遞給這個節點。 **不建議** 這樣做。
- **Thumbprint** - 將用來解密 _目標節點_ 上 DSC 設定中認證的憑證指紋。 **目標節點的本機電腦憑證存放區中必須有此憑證。**
- **CertificateFile** - 應用來加密 _目標節點_ 認證的憑證檔案 (僅包含公開金鑰)。 這必須是 DER 編碼的二進位 X.509 或 Base-64 編碼的 X.509 格式憑證檔案。

本範例會示範指定目標節點在具名的 targetNode 上動作的設定資料區塊、公開金鑰憑證檔案 (名為 targetNode.cer) 的路徑，以及公開金鑰的指紋。

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            }
        )
    }
```

## <a name="configuration-script"></a>設定指令碼

在設定指令碼中，使用 `PsCredential` 參數確保以最短的時間儲存認證。 當您執行提供的範例時，DSC 會提示您輸入認證，在設定資料區塊中使用與目標節點相關聯的 CertificateFile 來加密 MOF 檔案。 這個程式碼範例會從受保護的共用將檔案複製到使用者。

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a>設定解密

在 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) 能夠運作之前，您必須先使用 CertificateID 資源來驗證憑證的指紋，通知每個目標節點上的本機設定管理員要使用哪個憑證來將認證解密。 這個範例函式會尋找合適的本機憑證 (您可能需要自訂，讓它找到您想要使用的確切憑證)：

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

使用以指紋識別的憑證，設定指令碼可以更新成使用值：

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a>執行設定

此時，您可以執行設定，這樣會輸出兩個檔案：

- `*.meta.mof ` 檔案，其會使用儲存在本機電腦存放區且由其指紋識別的憑證，設定本機設定管理員來將認證解密。
  [Set-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/Set-DscLocalConfigurationManager) 會套用 `*.meta.mof ` 檔案。
- 實際套用設定的 MOF 檔案。 Start-DscConfiguration 會套用設定。

這些命令會完成這些步驟：

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

這個範例會將 DSC 設定推送至目標節點。 如果有一部 DSC 提取伺服器，也可以使用此伺服器套用 DSC 設定。

如需使用 DSC 提取伺服器套用 DSC 設定的詳細資訊，請參閱[設定 DSC 提取用戶端](pullClient.md)。

## <a name="credential-encryption-module-example"></a>認證加密模組範例

以下是完整的範例，包含所有的步驟，以及匯出及複製公開金鑰的協助程式 Cmdlet：

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)

    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
}

#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)

    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
        $certificates = dir Cert:\LocalMachine\my

        $certificates | %{
                    # Verify the certificate is for Encryption and valid
            if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
            {
                # Create the folder to hold the exported public key
                $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                if (! (Test-Path $folder))
                {
                    md $folder | Out-Null
                }

                # Export the public key to a well known location
                $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                # Return the thumbprint, and exported certificate path
                return @($_.Thumbprint,$certPath);
            }
        }
    }

    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
