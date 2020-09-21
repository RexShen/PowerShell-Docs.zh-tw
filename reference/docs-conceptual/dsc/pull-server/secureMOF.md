---
ms.date: 07/06/2020
keywords: dsc,powershell,設定,安裝
title: 保護 MOF 檔案
ms.openlocfilehash: b1319167010a85e639fdb51a1a0b8b472dfda3a6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778139"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="e3a93-103">保護 MOF 檔案</span><span class="sxs-lookup"><span data-stu-id="e3a93-103">Securing the MOF File</span></span>

> <span data-ttu-id="e3a93-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e3a93-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e3a93-105">DSC 會藉由套用儲存在 MOF 檔案中的資訊來管理伺服器節點的設定，而 MOF 檔案是本機系統管理員 (LCM) 實作所需結束狀態的位置。</span><span class="sxs-lookup"><span data-stu-id="e3a93-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span> <span data-ttu-id="e3a93-106">因為這個檔案包含設定的詳細資料，所以安全防護很重要。</span><span class="sxs-lookup"><span data-stu-id="e3a93-106">Because this file contains the details of the configuration, it's important to keep it secure.</span></span> <span data-ttu-id="e3a93-107">本主題說明如何確保目標節點加密檔案。</span><span class="sxs-lookup"><span data-stu-id="e3a93-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="e3a93-108">從 PowerShell 5.0 版開始，使用 `Start-DSCConfiguration` Cmdlet 將 MOF 檔案套用到節點時，預設會加密整個 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3a93-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="e3a93-109">當憑證未受管理，使用提取服務通訊協定來實作解決方案時，才需要文中所述的程序來確保目標節點所下載的設定在套用前能夠讓系統解密和讀取 (例如，Windows Server 提供的提取服務)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span> <span data-ttu-id="e3a93-110">向 [Azure 自動化 DSC](/azure/automation/automation-dsc-overview) 註冊的節點會自動安裝憑證，並交由服務管理而不需任何管理費用。</span><span class="sxs-lookup"><span data-stu-id="e3a93-110">Nodes registered to [Azure Automation DSC](/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="e3a93-111">本主題討論用於加密的憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-111">This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="e3a93-112">以自我簽署憑證進行加密便已足夠，因為私密金鑰一律會受到保護，且加密不代表信任文件。</span><span class="sxs-lookup"><span data-stu-id="e3a93-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="e3a93-113">自我簽署憑證_不能_用來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-113">Self-signed certificates should _not_ be used for authentication purposes.</span></span> <span data-ttu-id="e3a93-114">您應該使用來自信任憑證授權單位 (CA) 的憑證進行任何驗證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e3a93-115">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e3a93-115">Prerequisites</span></span>

<span data-ttu-id="e3a93-116">若要成功地加密用來保護 DSC 設定的認證，請確定您具備下列項目：</span><span class="sxs-lookup"><span data-stu-id="e3a93-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="e3a93-117">**發行與散發憑證的一些方法**。</span><span class="sxs-lookup"><span data-stu-id="e3a93-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="e3a93-118">本主題和範例假設您使用的是 Active Directory 憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="e3a93-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="e3a93-119">如需有關 Active Directory 憑證服務的詳細資訊，請參閱 [Active Directory 憑證服務概觀](https://technet.microsoft.com/library/hh831740.aspx)和 [Windows Server 2008 的 Active Directory 憑證服務](https://technet.microsoft.com/windowsserver/dd448615.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="e3a93-120">**目標節點或節點的系統管理存取權**。</span><span class="sxs-lookup"><span data-stu-id="e3a93-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="e3a93-121">**每個目標節點在其個人存放區都儲存了支援加密的憑證**。</span><span class="sxs-lookup"><span data-stu-id="e3a93-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="e3a93-122">在 Windows PowerShell 中，存放區的路徑是 Cert:\LocalMachine\My。</span><span class="sxs-lookup"><span data-stu-id="e3a93-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="e3a93-123">本主題中的範例會使用「工作站驗證」範本，您可在[預設憑證範本](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx)中找到它和其他憑證範本。</span><span class="sxs-lookup"><span data-stu-id="e3a93-123">The examples in this topic use the "workstation authentication" template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="e3a93-124">如果在目標節點以外的電腦上執行這項設定，請**匯出憑證的公開金鑰**，將它匯入要執行設定的電腦。</span><span class="sxs-lookup"><span data-stu-id="e3a93-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="e3a93-125">確定只匯出**公用**金鑰，妥善保管私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="e3a93-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

> [!NOTE]
> <span data-ttu-id="e3a93-126">指令碼資源具有一些加密限制。</span><span class="sxs-lookup"><span data-stu-id="e3a93-126">Script Resources have limitations when it comes to encryption.</span></span> <span data-ttu-id="e3a93-127">如需詳細資訊，請參閱[指令碼資源](../reference/resources/windows/scriptResource.md#known-limitations)</span><span class="sxs-lookup"><span data-stu-id="e3a93-127">For more information, see [Script Resource](../reference/resources/windows/scriptResource.md#known-limitations)</span></span>

## <a name="overall-process"></a><span data-ttu-id="e3a93-128">整體程序</span><span class="sxs-lookup"><span data-stu-id="e3a93-128">Overall process</span></span>

 1. <span data-ttu-id="e3a93-129">設定憑證、金鑰和指紋，並確定每個目標節點都有憑證複本，而設定電腦則有公開金鑰和指紋。</span><span class="sxs-lookup"><span data-stu-id="e3a93-129">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 1. <span data-ttu-id="e3a93-130">建立包含公開金鑰路徑和指紋的設定資料區塊。</span><span class="sxs-lookup"><span data-stu-id="e3a93-130">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 1. <span data-ttu-id="e3a93-131">建立為目標節點定義所需設定的設定指令碼，以及指揮本機設定管理員使用憑證及其指紋解密設定資料，設定目標節點的解密。</span><span class="sxs-lookup"><span data-stu-id="e3a93-131">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 1. <span data-ttu-id="e3a93-132">執行設定，會設定本機設定管理員的設定並啟動 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="e3a93-132">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![認證加密的程序流程](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="e3a93-134">憑證需求</span><span class="sxs-lookup"><span data-stu-id="e3a93-134">Certificate Requirements</span></span>

<span data-ttu-id="e3a93-135">若要制定認證加密，用來撰寫 DSC 設定之電腦所**信任**的_目標節點_上必須有公開金鑰憑證可用。</span><span class="sxs-lookup"><span data-stu-id="e3a93-135">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span> <span data-ttu-id="e3a93-136">此公開金鑰憑證具有可讓其用於 DSC 認證加密的特定需求︰</span><span class="sxs-lookup"><span data-stu-id="e3a93-136">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="e3a93-137">**金鑰使用方法**：</span><span class="sxs-lookup"><span data-stu-id="e3a93-137">**Key Usage**:</span></span>
   - <span data-ttu-id="e3a93-138">必須包含：'KeyEncipherment' 和 'DataEncipherment'。</span><span class="sxs-lookup"><span data-stu-id="e3a93-138">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="e3a93-139">「不得」包含：「數位簽章」。</span><span class="sxs-lookup"><span data-stu-id="e3a93-139">Should _not_ contain: 'Digital Signature'.</span></span>
1. <span data-ttu-id="e3a93-140">**增強金鑰使用方法**：</span><span class="sxs-lookup"><span data-stu-id="e3a93-140">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="e3a93-141">必須包含：文件加密 (1.3.6.1.4.1.311.80.1)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-141">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="e3a93-142">「不得」包含：用戶端驗證 (1.3.6.1.5.5.7.3.2) 與伺服器驗證 (1.3.6.1.5.5.7.3.1)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-142">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
1. <span data-ttu-id="e3a93-143">\*Target Node_ 上有憑證的私密金鑰可用。</span><span class="sxs-lookup"><span data-stu-id="e3a93-143">The Private Key for the certificate is available on the \*Target Node_.</span></span>
1. <span data-ttu-id="e3a93-144">憑證的**提供者**必須是「Microsoft RSA SChannel 密碼編譯提供者」。</span><span class="sxs-lookup"><span data-stu-id="e3a93-144">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3a93-145">雖然可使用的憑證，其含有「數位簽章」的金鑰使用方法，或驗證 EKU 的其中一個憑證，但這將導致加密金鑰更容易被誤用且很容易遭受攻擊。</span><span class="sxs-lookup"><span data-stu-id="e3a93-145">Although you can use a certificate containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="e3a93-146">因此，最佳做法是使用專為保護 DSC 認證所建立的憑證，來省略這些金鑰使用方法和 EKU。</span><span class="sxs-lookup"><span data-stu-id="e3a93-146">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="e3a93-147">您可以在_目標節點_上，使用符合這些準則的任何現有憑證來保護 DSC 認證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-147">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="e3a93-148">建立憑證</span><span class="sxs-lookup"><span data-stu-id="e3a93-148">Certificate creation</span></span>

<span data-ttu-id="e3a93-149">建立及使用必要的加密憑證 (成對的公用/私密金鑰組) 有兩種方法。</span><span class="sxs-lookup"><span data-stu-id="e3a93-149">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="e3a93-150">在**目標節點**上建立，並只將公用金鑰匯出至**撰寫節點**</span><span class="sxs-lookup"><span data-stu-id="e3a93-150">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
1. <span data-ttu-id="e3a93-151">在**撰寫節點**上建立，並將整組成對的金鑰匯出至**目標節點**</span><span class="sxs-lookup"><span data-stu-id="e3a93-151">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="e3a93-152">因為用於在 MOF 中解密認證的私密金鑰，會一直保存在目標節點中，所建議採用方法 1。</span><span class="sxs-lookup"><span data-stu-id="e3a93-152">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="e3a93-153">在目標節點上建立憑證</span><span class="sxs-lookup"><span data-stu-id="e3a93-153">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="e3a93-154">由於會使用私密金鑰在**目標節點**上將 MOF 解密，因此請務必確保其安全。最簡單的方法是在**目標節點**上建立私密金鑰憑證，並將**公開金鑰憑證**複製到用於將 DSC 設定撰寫入 MOF 檔案的電腦。</span><span class="sxs-lookup"><span data-stu-id="e3a93-154">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span> <span data-ttu-id="e3a93-155">下列範例將：</span><span class="sxs-lookup"><span data-stu-id="e3a93-155">The following example:</span></span>

1. <span data-ttu-id="e3a93-156">在**目標節點**上建立憑證</span><span class="sxs-lookup"><span data-stu-id="e3a93-156">creates a certificate on the **Target node**</span></span>
1. <span data-ttu-id="e3a93-157">在**目標節點**上匯出公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-157">exports the public key certificate on the **Target node**.</span></span>
1. <span data-ttu-id="e3a93-158">在**撰寫節點**上將公開金鑰憑證匯入**我的**憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e3a93-158">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="e3a93-159">在目標節點上︰ 建立及匯出憑證</span><span class="sxs-lookup"><span data-stu-id="e3a93-159">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="e3a93-160">目標節點：Windows Server 2016 與 Windows 10</span><span class="sxs-lookup"><span data-stu-id="e3a93-160">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="e3a93-161">匯出之後，必須將 `DscPublicKey.cer` 複製到**撰寫節點**。</span><span class="sxs-lookup"><span data-stu-id="e3a93-161">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="e3a93-162">目標節點：Windows Server 2012 R2/Windows 8.1 及更早版本</span><span class="sxs-lookup"><span data-stu-id="e3a93-162">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

> [!WARNING]
> <span data-ttu-id="e3a93-163">因為在比 Windows 10 和 Windows Server 2016 更早的 Windows 作業系統上，`New-SelfSignedCertificate` Cmdlet 不支援 **Type** 參數，所以在這些作業系統上需要建立此憑證的替代方法。</span><span class="sxs-lookup"><span data-stu-id="e3a93-163">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="e3a93-164">在此情況下，可以使用 `makecert.exe` 或 `certutil.exe` 來建立憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-164">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="e3a93-165">替代方法是[從 Microsoft 指令碼中心下載 New-SelfSignedCertificateEx.ps1 指令碼](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6)，並改用它來建立憑證︰</span><span class="sxs-lookup"><span data-stu-id="e3a93-165">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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

<span data-ttu-id="e3a93-166">匯出之後，必須將 ```DscPublicKey.cer``` 複製到**撰寫節點**。</span><span class="sxs-lookup"><span data-stu-id="e3a93-166">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="e3a93-167">在撰寫節點上︰匯入憑證的公開金鑰</span><span class="sxs-lookup"><span data-stu-id="e3a93-167">On the Authoring Node: import the cert's public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="e3a93-168">在撰寫節點上建立憑證</span><span class="sxs-lookup"><span data-stu-id="e3a93-168">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="e3a93-169">或者，在**撰寫節點**上建立加密憑證，搭配**私密金鑰**作為 PFX 檔案進行匯出，然後再匯入到**目標節點**上。</span><span class="sxs-lookup"><span data-stu-id="e3a93-169">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span> <span data-ttu-id="e3a93-170">這是目前在 _Nano Server_ 上實作 DSC 認證加密的方法。</span><span class="sxs-lookup"><span data-stu-id="e3a93-170">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span> <span data-ttu-id="e3a93-171">雖然有使用密碼保護 PFX，在傳輸期間也應該保持安全狀態。</span><span class="sxs-lookup"><span data-stu-id="e3a93-171">Although the PFX is secured with a password it should be kept secure during transit.</span></span> <span data-ttu-id="e3a93-172">下列範例將：</span><span class="sxs-lookup"><span data-stu-id="e3a93-172">The following example:</span></span>

1. <span data-ttu-id="e3a93-173">在**撰寫節點**上建立憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-173">creates a certificate on the **Authoring node**.</span></span>
1. <span data-ttu-id="e3a93-174">在**撰寫節點**上匯出包含私密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-174">exports the certificate including the private key on the **Authoring node**.</span></span>
1. <span data-ttu-id="e3a93-175">從**製作節點**移除私密金鑰 ，但保留**我的**存放區中之公開金鑰憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-175">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
1. <span data-ttu-id="e3a93-176">將私密金鑰憑證匯入**目標節點**上我的 (個人) 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="e3a93-176">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="e3a93-177">它必須加入根存放區，才會得到**目標節點**的信任。</span><span class="sxs-lookup"><span data-stu-id="e3a93-177">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="e3a93-178">在撰寫節點上：建立及匯出憑證</span><span class="sxs-lookup"><span data-stu-id="e3a93-178">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="e3a93-179">目標節點：Windows Server 2016 與 Windows 10</span><span class="sxs-lookup"><span data-stu-id="e3a93-179">Target Node: Windows Server 2016 and Windows 10</span></span>

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

<span data-ttu-id="e3a93-180">匯出之後，必須將 `DscPrivateKey.pfx` 複製到**目標節點**。</span><span class="sxs-lookup"><span data-stu-id="e3a93-180">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="e3a93-181">目標節點：Windows Server 2012 R2/Windows 8.1 及更早版本</span><span class="sxs-lookup"><span data-stu-id="e3a93-181">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

> [!WARNING]
> <span data-ttu-id="e3a93-182">因為在比 Windows 10 和 Windows Server 2016 更早的 Windows 作業系統上，`New-SelfSignedCertificate` Cmdlet 不支援 **Type** 參數，所以在這些作業系統上需要建立此憑證的替代方法。</span><span class="sxs-lookup"><span data-stu-id="e3a93-182">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="e3a93-183">在此情況下，可以使用 `makecert.exe` 或 `certutil.exe` 來建立憑證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-183">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="e3a93-184">替代方法是[從 Microsoft 指令碼中心下載 New-SelfSignedCertificateEx.ps1 指令碼](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6)，並改用它來建立憑證︰</span><span class="sxs-lookup"><span data-stu-id="e3a93-184">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="e3a93-185">在目標節點上︰匯入憑證的私密金鑰作為受信任的根</span><span class="sxs-lookup"><span data-stu-id="e3a93-185">On the Target Node: import the cert's private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="e3a93-186">設定資料</span><span class="sxs-lookup"><span data-stu-id="e3a93-186">Configuration data</span></span>

<span data-ttu-id="e3a93-187">設定資料區塊會定義哪些是執行作業的目標節點、是否加密認證、加密方法和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e3a93-187">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="e3a93-188">如需設定資料區塊的詳細資訊，請參閱[分離設定和環境資料](../configurations/configData.md)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-188">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="e3a93-189">可為每個認證加密相關節點進行設定的項目包括：</span><span class="sxs-lookup"><span data-stu-id="e3a93-189">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="e3a93-190">**NodeName** - 要設定認證加密的目標節點名稱。</span><span class="sxs-lookup"><span data-stu-id="e3a93-190">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="e3a93-191">**PsDscAllowPlainTextPassword** - 是否允許將未加密的認證傳遞給這個節點。</span><span class="sxs-lookup"><span data-stu-id="e3a93-191">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="e3a93-192">**不建議**這樣做。</span><span class="sxs-lookup"><span data-stu-id="e3a93-192">This is **not recommended**.</span></span>
- <span data-ttu-id="e3a93-193">**Thumbprint** - 將用來解密_目標節點_上 DSC 設定中認證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="e3a93-193">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="e3a93-194">**目標節點的本機電腦憑證存放區中必須有此憑證。**</span><span class="sxs-lookup"><span data-stu-id="e3a93-194">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="e3a93-195">**CertificateFile** - 應用來加密_目標節點_認證的憑證檔案 (僅包含公開金鑰)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-195">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="e3a93-196">這必須是 DER 編碼的二進位 X.509 或 Base-64 編碼的 X.509 格式憑證檔案。</span><span class="sxs-lookup"><span data-stu-id="e3a93-196">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="e3a93-197">本範例會示範指定目標節點在具名的 targetNode 上動作的設定資料區塊、公開金鑰憑證檔案 (名為 targetNode.cer) 的路徑，以及公開金鑰的指紋。</span><span class="sxs-lookup"><span data-stu-id="e3a93-197">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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

## <a name="configuration-script"></a><span data-ttu-id="e3a93-198">設定指令碼</span><span class="sxs-lookup"><span data-stu-id="e3a93-198">Configuration script</span></span>

<span data-ttu-id="e3a93-199">在設定指令碼中，使用 `PsCredential` 參數確保以最短的時間儲存認證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-199">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="e3a93-200">當您執行提供的範例時，DSC 會提示您輸入認證，在設定資料區塊中使用與目標節點相關聯的 CertificateFile 來加密 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3a93-200">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="e3a93-201">這個程式碼範例會從受保護的共用將檔案複製到使用者。</span><span class="sxs-lookup"><span data-stu-id="e3a93-201">This code example copies a file from a share that is secured to a user.</span></span>

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

## <a name="setting-up-decryption"></a><span data-ttu-id="e3a93-202">設定解密</span><span class="sxs-lookup"><span data-stu-id="e3a93-202">Setting up decryption</span></span>

<span data-ttu-id="e3a93-203">您必須先使用 CertificateID 資源來驗證憑證的指紋，通知每個目標節點上的本機設定管理員要使用哪項憑證來解密認證，[`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) 才能運作。</span><span class="sxs-lookup"><span data-stu-id="e3a93-203">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate's thumbprint.</span></span> <span data-ttu-id="e3a93-204">這個範例函式會尋找合適的本機憑證 (您可能需要自訂，讓它找到您想要使用的確切憑證)：</span><span class="sxs-lookup"><span data-stu-id="e3a93-204">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="e3a93-205">使用以指紋識別的憑證，設定指令碼可以更新成使用值：</span><span class="sxs-lookup"><span data-stu-id="e3a93-205">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="e3a93-206">執行設定</span><span class="sxs-lookup"><span data-stu-id="e3a93-206">Running the configuration</span></span>

<span data-ttu-id="e3a93-207">此時，您可以執行設定，這樣會輸出兩個檔案：</span><span class="sxs-lookup"><span data-stu-id="e3a93-207">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="e3a93-208">\*.meta.mof 檔案，使用儲存在本機電腦存放區以指紋識別的憑證，設定本機設定管理員來解密認證。</span><span class="sxs-lookup"><span data-stu-id="e3a93-208">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span>
  <span data-ttu-id="e3a93-209">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) 會套用 \*.meta.mof 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3a93-209">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="e3a93-210">實際套用設定的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3a93-210">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="e3a93-211">Start-DscConfiguration 會套用設定。</span><span class="sxs-lookup"><span data-stu-id="e3a93-211">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="e3a93-212">這些命令會完成這些步驟：</span><span class="sxs-lookup"><span data-stu-id="e3a93-212">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="e3a93-213">這個範例會將 DSC 設定推送至目標節點。</span><span class="sxs-lookup"><span data-stu-id="e3a93-213">This example would push the DSC configuration to the target node.</span></span> <span data-ttu-id="e3a93-214">如果有一部 DSC 提取伺服器，也可以使用此伺服器套用 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="e3a93-214">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="e3a93-215">如需使用 DSC 提取伺服器套用 DSC 設定的詳細資訊，請參閱[設定 DSC 提取用戶端](pullClient.md)。</span><span class="sxs-lookup"><span data-stu-id="e3a93-215">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="e3a93-216">認證加密模組範例</span><span class="sxs-lookup"><span data-stu-id="e3a93-216">Credential Encryption Module Example</span></span>

<span data-ttu-id="e3a93-217">以下是完整的範例，包含所有的步驟，以及匯出及複製公開金鑰的協助程式 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="e3a93-217">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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
