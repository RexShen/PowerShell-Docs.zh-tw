---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定資料的認證選項
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "55677029"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="01d5f-103">設定資料的認證選項</span><span class="sxs-lookup"><span data-stu-id="01d5f-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="01d5f-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="01d5f-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="01d5f-105">純文字密碼和網域使用者</span><span class="sxs-lookup"><span data-stu-id="01d5f-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="01d5f-106">包含未加密認證的 DSC 設定會產生有關純文字密碼的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="01d5f-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="01d5f-107">DSC 也會在使用網域認證時產生警告。</span><span class="sxs-lookup"><span data-stu-id="01d5f-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="01d5f-108">若要隱藏這些錯誤和警告訊息，請使用 DSC 設定資料關鍵字：</span><span class="sxs-lookup"><span data-stu-id="01d5f-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="01d5f-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="01d5f-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="01d5f-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="01d5f-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="01d5f-111">儲存/傳輸未加密的純文字密碼通常是不安全的。</span><span class="sxs-lookup"><span data-stu-id="01d5f-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="01d5f-112">建議您使用本主題稍後所涵蓋的技術來保護認證。</span><span class="sxs-lookup"><span data-stu-id="01d5f-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="01d5f-113">Azure Automation DSC 服務能讓您集中管理及安全儲存要在設定中編譯的認證。</span><span class="sxs-lookup"><span data-stu-id="01d5f-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="01d5f-114">如需資訊，請參閱：[編譯 DSC 設定/認證資產](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="01d5f-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="01d5f-115">處理 DSC 的認證</span><span class="sxs-lookup"><span data-stu-id="01d5f-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="01d5f-116">DSC 設定資源預設執行為 `Local System`。</span><span class="sxs-lookup"><span data-stu-id="01d5f-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="01d5f-117">不過，有些資源需要認證，例如當 `Package` 資源需要在特定使用者帳戶下安裝軟體時。</span><span class="sxs-lookup"><span data-stu-id="01d5f-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="01d5f-118">資源過去使用硬式編碼的 `Credential` 屬性名稱來處理這種情形。</span><span class="sxs-lookup"><span data-stu-id="01d5f-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="01d5f-119">WMF 5.0 為所有資源加入了自動的 `PsDscRunAsCredential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="01d5f-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="01d5f-120">如需關於使用 `PsDscRunAsCredential` 的相關資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="01d5f-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="01d5f-121">較新的資源和自訂的資源可以使用這個自動屬性，不用建立自己專有的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="01d5f-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="01d5f-122">某些資源的目的是為特定原因使用多個認證，所以會有自己的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="01d5f-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="01d5f-123">若要在資源上尋找可用的認證屬性，請使用 `Get-DscResource -Name ResourceName -Syntax` 或 ISE 的 Intellisense (`CTRL+SPACE`)。</span><span class="sxs-lookup"><span data-stu-id="01d5f-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
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

<span data-ttu-id="01d5f-124">本例使用 `PSDesiredStateConfiguration` 內建 DSC 資源模組的 [Group](../resources/resources.md) 資源。</span><span class="sxs-lookup"><span data-stu-id="01d5f-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="01d5f-125">它會建立本機群組並新增或移除成員。</span><span class="sxs-lookup"><span data-stu-id="01d5f-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="01d5f-126">它接受 `Credential` 屬性和自動的 `PsDscRunAsCredential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="01d5f-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="01d5f-127">不過，資源只會使用 `Credential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="01d5f-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="01d5f-128">如需 `PsDscRunAsCredential` 屬性的詳細資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="01d5f-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="01d5f-129">範例：Group 資源 Credential 屬性</span><span class="sxs-lookup"><span data-stu-id="01d5f-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="01d5f-130">DSC 在 `Local System` 下執行，所以它已有可變更本機使用者和群組的權限。</span><span class="sxs-lookup"><span data-stu-id="01d5f-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="01d5f-131">如果新增成員是本機帳戶，就不需要認證。</span><span class="sxs-lookup"><span data-stu-id="01d5f-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="01d5f-132">如果 `Group` 資源在本機群組中加入網域帳戶，就需要認證。</span><span class="sxs-lookup"><span data-stu-id="01d5f-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="01d5f-133">Active Directory 不允許匿名查詢。</span><span class="sxs-lookup"><span data-stu-id="01d5f-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="01d5f-134">`Group` 資源的 `Credential` 屬性是用來查詢 Active Directory 的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="01d5f-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="01d5f-135">就多數情況而言，這可能是一般的使用者帳戶，因為使用者預設可以*讀取* Active Directory 大部分的物件。</span><span class="sxs-lookup"><span data-stu-id="01d5f-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="01d5f-136">設定範例</span><span class="sxs-lookup"><span data-stu-id="01d5f-136">Example Configuration</span></span>

<span data-ttu-id="01d5f-137">以下程式碼範例會使用 DSC 以網域使用者填入本機群組：</span><span class="sxs-lookup"><span data-stu-id="01d5f-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="01d5f-138">這個程式碼會產生錯誤和警告訊息：</span><span class="sxs-lookup"><span data-stu-id="01d5f-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="01d5f-139">本範例有兩個問題：</span><span class="sxs-lookup"><span data-stu-id="01d5f-139">This example has two issues:</span></span>

1. <span data-ttu-id="01d5f-140">錯誤說明不建議純文字密碼</span><span class="sxs-lookup"><span data-stu-id="01d5f-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="01d5f-141">警告建議不要使用網域認證</span><span class="sxs-lookup"><span data-stu-id="01d5f-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="01d5f-142">旗標**PSDSCAllowPlainTextPassword**並**PSDSCAllowDomainUser**隱藏錯誤和警告通知所涉及的風險的使用者。</span><span class="sxs-lookup"><span data-stu-id="01d5f-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="01d5f-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="01d5f-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="01d5f-144">第一個錯誤訊息有文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="01d5f-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="01d5f-145">這個連結說明如何使用 [ConfigurationData](./configData.md) 結構和憑證加密密碼。</span><span class="sxs-lookup"><span data-stu-id="01d5f-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="01d5f-146">如需憑證和 DSC 的詳細資訊，請[閱讀這篇文章](http://aka.ms/certs4dsc)。</span><span class="sxs-lookup"><span data-stu-id="01d5f-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="01d5f-147">若要強制施作純文字密碼，資源在設定資料區段中需要有 `PsDscAllowPlainTextPassword` 關鍵字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="01d5f-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="01d5f-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="01d5f-148">localhost.mof</span></span>

<span data-ttu-id="01d5f-149">**PSDSCAllowPlainTextPassword**旗標會要求使用者確認在 MOF 檔案中儲存純文字密碼的風險。</span><span class="sxs-lookup"><span data-stu-id="01d5f-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="01d5f-150">在產生的 MOF 檔案中，即使**PSCredential**物件，包含**SecureString**使用，密碼仍然會顯示為純文字。</span><span class="sxs-lookup"><span data-stu-id="01d5f-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="01d5f-151">這是唯一的認證已公開的時間。</span><span class="sxs-lookup"><span data-stu-id="01d5f-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="01d5f-152">使其無法存取此 MOF 檔案可讓任何人存取的系統管理員帳戶。</span><span class="sxs-lookup"><span data-stu-id="01d5f-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="01d5f-153">傳輸中和待用的認證</span><span class="sxs-lookup"><span data-stu-id="01d5f-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="01d5f-154">**PSDscAllowPlainTextPassword**旗標可讓編譯的 MOF 檔案，其中包含以純文字密碼。</span><span class="sxs-lookup"><span data-stu-id="01d5f-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="01d5f-155">將包含純文字密碼的 MOF 檔案儲存時，請採取預防措施。</span><span class="sxs-lookup"><span data-stu-id="01d5f-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="01d5f-156">傳遞的 MOF 檔案中的節點的時機**推播**模式中，WinRM 加密來保護的純文字密碼，除非您覆寫預設的通訊**AllowUnencrypted**參數。</span><span class="sxs-lookup"><span data-stu-id="01d5f-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="01d5f-157">加密的 MOF 使用憑證保護待用的 MOF 檔案，套用到節點之前。</span><span class="sxs-lookup"><span data-stu-id="01d5f-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="01d5f-158">在 **提取**模式中，您可以設定 Windows 提取伺服器，以使用 HTTPS 來加密使用 Internet Information Server 中所指定的通訊協定的流量。</span><span class="sxs-lookup"><span data-stu-id="01d5f-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="01d5f-159">如需詳細資訊，請參閱文章[設定 DSC 提取用戶端](../pull-server/pullclient.md)並[使用憑證保護 MOF 檔案](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="01d5f-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="01d5f-160">在  [Azure 自動化狀態設定](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)服務，則提取一律會加密流量。</span><span class="sxs-lookup"><span data-stu-id="01d5f-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="01d5f-161">在節點上待用加密 MOF 檔案從 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="01d5f-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="01d5f-162">在 PowerShell 4.0 的 MOF 檔案是待用加密，除非推送或提取至節點時，使用憑證加密它們。</span><span class="sxs-lookup"><span data-stu-id="01d5f-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="01d5f-163">**Microsoft 不建議您使用純文字密碼，以免造成嚴重的安全性風險。**</span><span class="sxs-lookup"><span data-stu-id="01d5f-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="01d5f-164">網域認證</span><span class="sxs-lookup"><span data-stu-id="01d5f-164">Domain Credentials</span></span>

<span data-ttu-id="01d5f-165">再次執行範例設定指令碼 (加密或不加密)，仍會產生警告，指出不建議使用網域帳戶進行認證。</span><span class="sxs-lookup"><span data-stu-id="01d5f-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="01d5f-166">使用本機帳戶可降低暴露其他伺服器也可使用之網域認證的可能性。</span><span class="sxs-lookup"><span data-stu-id="01d5f-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="01d5f-167">**認證搭配 DSC 資源使用時，請盡可能使用本機帳戶，而不用網域帳戶。**</span><span class="sxs-lookup"><span data-stu-id="01d5f-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="01d5f-168">若認證的 `Username` 屬性中有 '\\' 或 '\@'，則 DSC 會將它視為網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="01d5f-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="01d5f-169">使用者名稱的網域部分為 "localhost"、"127.0.0.1" 和 "::1" 時例外。</span><span class="sxs-lookup"><span data-stu-id="01d5f-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="01d5f-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="01d5f-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="01d5f-171">在上述的 DSC `Group` 資源範例中，查詢 Active Directory 網域*需要*網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="01d5f-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="01d5f-172">發生這種情況時，請將 `PSDscAllowDomainUser` 屬性加入 `ConfigurationData` 區塊中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="01d5f-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="01d5f-173">現在設定指令碼產生的 MOF 檔案不再有任何錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="01d5f-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
