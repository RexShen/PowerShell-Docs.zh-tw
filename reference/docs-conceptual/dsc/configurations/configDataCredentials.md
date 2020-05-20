---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定資料的認證選項
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870552"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="78720-103">設定資料的認證選項</span><span class="sxs-lookup"><span data-stu-id="78720-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="78720-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="78720-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="78720-105">純文字密碼和網域使用者</span><span class="sxs-lookup"><span data-stu-id="78720-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="78720-106">包含未加密認證的 DSC 設定會產生有關純文字密碼的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="78720-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="78720-107">DSC 也會在使用網域認證時產生警告。</span><span class="sxs-lookup"><span data-stu-id="78720-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="78720-108">若要隱藏這些錯誤和警告訊息，請使用 DSC 設定資料關鍵字：</span><span class="sxs-lookup"><span data-stu-id="78720-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="78720-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="78720-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="78720-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="78720-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="78720-111">儲存/傳輸未加密的純文字密碼通常是不安全的。</span><span class="sxs-lookup"><span data-stu-id="78720-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="78720-112">建議您使用本主題稍後所涵蓋的技術來保護認證。</span><span class="sxs-lookup"><span data-stu-id="78720-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="78720-113">Azure Automation DSC 服務能讓您集中管理及安全儲存要在設定中編譯的認證。</span><span class="sxs-lookup"><span data-stu-id="78720-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="78720-114">如需資訊，請參閱：[編譯 DSC 設定/認證資產](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="78720-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="78720-115">處理 DSC 的認證</span><span class="sxs-lookup"><span data-stu-id="78720-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="78720-116">DSC 設定資源預設執行為 `Local System`。</span><span class="sxs-lookup"><span data-stu-id="78720-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="78720-117">不過，有些資源需要認證，例如當 `Package` 資源需要在特定使用者帳戶下安裝軟體時。</span><span class="sxs-lookup"><span data-stu-id="78720-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="78720-118">資源過去使用硬式編碼的 `Credential` 屬性名稱來處理這種情形。</span><span class="sxs-lookup"><span data-stu-id="78720-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="78720-119">WMF 5.0 為所有資源加入了自動的 `PsDscRunAsCredential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="78720-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="78720-120">如需關於使用 `PsDscRunAsCredential` 的相關資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="78720-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="78720-121">較新的資源和自訂的資源可以使用這個自動屬性，不用建立自己專有的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="78720-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="78720-122">某些資源的目的是為特定原因使用多個認證，所以會有自己的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="78720-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="78720-123">若要在資源上尋找可用的認證屬性，請使用 `Get-DscResource -Name ResourceName -Syntax` 或 ISE 的 Intellisense (`CTRL+SPACE`)。</span><span class="sxs-lookup"><span data-stu-id="78720-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="78720-124">本例使用 `PSDesiredStateConfiguration` 內建 DSC 資源模組的 [Group](../resources/resources.md) 資源。</span><span class="sxs-lookup"><span data-stu-id="78720-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="78720-125">它會建立本機群組並新增或移除成員。</span><span class="sxs-lookup"><span data-stu-id="78720-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="78720-126">它接受 `Credential` 屬性和自動的 `PsDscRunAsCredential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="78720-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="78720-127">不過，資源只會使用 `Credential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="78720-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="78720-128">如需 `PsDscRunAsCredential` 屬性的詳細資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="78720-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="78720-129">範例：Group 資源 Credential 屬性</span><span class="sxs-lookup"><span data-stu-id="78720-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="78720-130">DSC 在 `Local System` 下執行，所以它已有可變更本機使用者和群組的權限。</span><span class="sxs-lookup"><span data-stu-id="78720-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="78720-131">如果新增成員是本機帳戶，就不需要認證。</span><span class="sxs-lookup"><span data-stu-id="78720-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="78720-132">如果 `Group` 資源在本機群組中加入網域帳戶，就需要認證。</span><span class="sxs-lookup"><span data-stu-id="78720-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="78720-133">Active Directory 不允許匿名查詢。</span><span class="sxs-lookup"><span data-stu-id="78720-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="78720-134">`Group` 資源的 `Credential` 屬性是用來查詢 Active Directory 的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="78720-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="78720-135">就多數情況而言，這可能是一般的使用者帳戶，因為使用者預設可以*讀取* Active Directory 大部分的物件。</span><span class="sxs-lookup"><span data-stu-id="78720-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="78720-136">設定範例</span><span class="sxs-lookup"><span data-stu-id="78720-136">Example Configuration</span></span>

<span data-ttu-id="78720-137">以下程式碼範例會使用 DSC 以網域使用者填入本機群組：</span><span class="sxs-lookup"><span data-stu-id="78720-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

<span data-ttu-id="78720-138">這個程式碼會產生錯誤和警告訊息：</span><span class="sxs-lookup"><span data-stu-id="78720-138">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

<span data-ttu-id="78720-139">本範例有兩個問題：</span><span class="sxs-lookup"><span data-stu-id="78720-139">This example has two issues:</span></span>

1. <span data-ttu-id="78720-140">錯誤說明不建議純文字密碼</span><span class="sxs-lookup"><span data-stu-id="78720-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="78720-141">警告建議不要使用網域認證</span><span class="sxs-lookup"><span data-stu-id="78720-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="78720-142">旗標 **PSDSCAllowPlainTextPassword** 和 **PSDSCAllowDomainUser** 會隱藏錯誤和警告，通知使用者所涉及的風險。</span><span class="sxs-lookup"><span data-stu-id="78720-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="78720-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="78720-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="78720-144">第一個錯誤訊息有文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="78720-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="78720-145">這個連結說明如何使用 [ConfigurationData](./configData.md) 結構和憑證加密密碼。</span><span class="sxs-lookup"><span data-stu-id="78720-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="78720-146">如需憑證和 DSC 的詳細資訊，請[閱讀這篇文章](https://aka.ms/certs4dsc)。</span><span class="sxs-lookup"><span data-stu-id="78720-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="78720-147">若要強制施作純文字密碼，資源在設定資料區段中需要有 `PsDscAllowPlainTextPassword` 關鍵字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="78720-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a><span data-ttu-id="78720-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="78720-148">localhost.mof</span></span>

<span data-ttu-id="78720-149">**PSDSCAllowPlainTextPassword** 旗標會要求使用者確認將純文字密碼儲存在 MOF 檔案中的風險。</span><span class="sxs-lookup"><span data-stu-id="78720-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="78720-150">在產生的 MOF 檔案中，即使使用包含 **SecureString** 的 **PSCredential** 物件，密碼仍然會顯示為純文字。</span><span class="sxs-lookup"><span data-stu-id="78720-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="78720-151">這是公開認證的唯一時間。</span><span class="sxs-lookup"><span data-stu-id="78720-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="78720-152">取得對此 MOF 檔案的存取權限，可讓任何人存取系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="78720-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="78720-153">傳輸中和待用的認證</span><span class="sxs-lookup"><span data-stu-id="78720-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="78720-154">**PSDscAllowPlainTextPassword** 旗標允許編譯包含純文字密碼的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="78720-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="78720-155">儲存包含純文字密碼的 MOF 檔案時，請採取預防措施。</span><span class="sxs-lookup"><span data-stu-id="78720-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="78720-156">當 MOF 檔案以**推送**模式傳送到節點時，WinRM 會加密通訊以保護純文字密碼，除非您使用 **AllowUnencrypted** 參數覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="78720-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="78720-157">使用憑證加密 MOF，可以在 MOF 檔案套用到節點之前保護待用檔案。</span><span class="sxs-lookup"><span data-stu-id="78720-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="78720-158">在**提取**模式中，您可以將 Windows 提取伺服器設定為使用 HTTPS，以使用 Internet Information Server 中所指定的通訊協定來加密流量。</span><span class="sxs-lookup"><span data-stu-id="78720-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="78720-159">如需詳細資訊，請參閱[設定 DSC 提取用戶端](../pull-server/pullclient.md)和[使用憑證保護 MOF 檔案](../pull-server/secureMOF.md)文章。</span><span class="sxs-lookup"><span data-stu-id="78720-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="78720-160">在 [Azure 自動化狀態設定](/azure/automation/automation-dsc-overview) \(機器翻譯\) 服務中，提取流量一律會加密。</span><span class="sxs-lookup"><span data-stu-id="78720-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="78720-161">在節點上，MOF 檔案在待用時加密 (從 PowerShell 5.0 開始)。</span><span class="sxs-lookup"><span data-stu-id="78720-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="78720-162">在 PowerShell 4.0 中，MOF 檔案在待用時是未加密的，除非它們在推送或提取至節點時使用憑證加密。</span><span class="sxs-lookup"><span data-stu-id="78720-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="78720-163">**Microsoft 不建議您使用純文字密碼，以免造成嚴重的安全性風險。**</span><span class="sxs-lookup"><span data-stu-id="78720-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="78720-164">網域認證</span><span class="sxs-lookup"><span data-stu-id="78720-164">Domain Credentials</span></span>

<span data-ttu-id="78720-165">再次執行範例設定指令碼 (加密或不加密)，仍會產生警告，指出不建議使用網域帳戶進行認證。</span><span class="sxs-lookup"><span data-stu-id="78720-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="78720-166">使用本機帳戶可降低暴露其他伺服器也可使用之網域認證的可能性。</span><span class="sxs-lookup"><span data-stu-id="78720-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="78720-167">**認證搭配 DSC 資源使用時，請盡可能使用本機帳戶，而不用網域帳戶。**</span><span class="sxs-lookup"><span data-stu-id="78720-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="78720-168">若認證的 `Username` 屬性中有 '\\' 或 '\@'，則 DSC 會將它視為網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="78720-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="78720-169">使用者名稱的網域部分為 "localhost"、"127.0.0.1" 和 "::1" 時例外。</span><span class="sxs-lookup"><span data-stu-id="78720-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="78720-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="78720-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="78720-171">在上述的 DSC `Group` 資源範例中，查詢 Active Directory 網域*需要*網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="78720-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="78720-172">發生這種情況時，請將 `PSDscAllowDomainUser` 屬性加入 `ConfigurationData` 區塊中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="78720-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

<span data-ttu-id="78720-173">現在設定指令碼產生的 MOF 檔案不再有任何錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="78720-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
