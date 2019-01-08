---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定資料的認證選項
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046636"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="f674e-103">設定資料的認證選項</span><span class="sxs-lookup"><span data-stu-id="f674e-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="f674e-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f674e-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="f674e-105">純文字密碼和網域使用者</span><span class="sxs-lookup"><span data-stu-id="f674e-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="f674e-106">包含未加密認證的 DSC 設定會產生有關純文字密碼的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f674e-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="f674e-107">DSC 也會在使用網域認證時產生警告。</span><span class="sxs-lookup"><span data-stu-id="f674e-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="f674e-108">若要隱藏這些錯誤和警告訊息，請使用 DSC 設定資料關鍵字：</span><span class="sxs-lookup"><span data-stu-id="f674e-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="f674e-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="f674e-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="f674e-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="f674e-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="f674e-111">儲存/傳輸未加密的純文字密碼通常是不安全的。</span><span class="sxs-lookup"><span data-stu-id="f674e-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="f674e-112">建議您使用本主題稍後所涵蓋的技術來保護認證。</span><span class="sxs-lookup"><span data-stu-id="f674e-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="f674e-113">Azure Automation DSC 服務能讓您集中管理及安全儲存要在設定中編譯的認證。</span><span class="sxs-lookup"><span data-stu-id="f674e-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="f674e-114">如需詳細資訊，請參閱：[編譯 DSC 組態 / 認證資產](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="f674e-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="f674e-115">傳遞純文字認證的範例如下︰</span><span class="sxs-lookup"><span data-stu-id="f674e-115">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
            @{
                # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
                NodeName="*"
                PSDscAllowPlainTextPassword = $true
            },
            #however, each node still needs to be explicitly defined for "*" to have meaning
            @{
                NodeName = "TestMachine1"
            },
            #we can also use a property to define node-specific passwords, although this is no more secure
            @{
                NodeName = "TestMachine2";
                UserName = "User2"
                LocalPassword = "ThisIsYetAnotherPlaintextPassword"
            }
        )
}

configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="f674e-116">這是 「 TestMachine1"的組態所產生的 「.mof 」 檔案的摘錄。</span><span class="sxs-lookup"><span data-stu-id="f674e-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="f674e-117">`System.Security.SecureString`中所使用的組態已轉換為純文字並儲存在 「.mof 」 檔案，為`MSF_Credential`。</span><span class="sxs-lookup"><span data-stu-id="f674e-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="f674e-118">A`SecureString`加密與目前的使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="f674e-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="f674e-119">這適用於所有形式的 PowerShell 遠端管理。</span><span class="sxs-lookup"><span data-stu-id="f674e-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="f674e-120">「.mof"檔案被設計為獨立單獨的組態設定機制。</span><span class="sxs-lookup"><span data-stu-id="f674e-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="f674e-121">從 PowerShell 5.0 開始，在節點上的 「.mof"檔案會加密待用的情況下，而不是在傳輸至節點。</span><span class="sxs-lookup"><span data-stu-id="f674e-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="f674e-122">這表示 「.mof 」 檔案中的密碼會公開成純文字，當您將它們套用至節點。</span><span class="sxs-lookup"><span data-stu-id="f674e-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="f674e-123">若要加密的認證，您必須使用**提取伺服器**。</span><span class="sxs-lookup"><span data-stu-id="f674e-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="f674e-124">如需詳細資訊，請參閱 <<c0> [ 使用憑證保護 MOF 檔案](../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="f674e-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="f674e-125">處理 DSC 的認證</span><span class="sxs-lookup"><span data-stu-id="f674e-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="f674e-126">DSC 設定資源預設執行為 `Local System`。</span><span class="sxs-lookup"><span data-stu-id="f674e-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="f674e-127">不過，有些資源需要認證，例如當 `Package` 資源需要在特定使用者帳戶下安裝軟體時。</span><span class="sxs-lookup"><span data-stu-id="f674e-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="f674e-128">資源過去使用硬式編碼的 `Credential` 屬性名稱來處理這種情形。</span><span class="sxs-lookup"><span data-stu-id="f674e-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="f674e-129">WMF 5.0 為所有資源加入了自動的 `PsDscRunAsCredential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f674e-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="f674e-130">如需關於使用 `PsDscRunAsCredential` 的相關資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="f674e-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="f674e-131">較新的資源和自訂的資源可以使用這個自動屬性，不用建立自己專有的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="f674e-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="f674e-132">某些資源的目的是為特定原因使用多個認證，所以會有自己的認證屬性。</span><span class="sxs-lookup"><span data-stu-id="f674e-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="f674e-133">若要在資源上尋找可用的認證屬性，請使用 `Get-DscResource -Name ResourceName -Syntax` 或 ISE 的 Intellisense (`CTRL+SPACE`)。</span><span class="sxs-lookup"><span data-stu-id="f674e-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="f674e-134">本例使用 `PSDesiredStateConfiguration` 內建 DSC 資源模組的 [Group](../resources/resources.md) 資源。</span><span class="sxs-lookup"><span data-stu-id="f674e-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="f674e-135">它會建立本機群組並新增或移除成員。</span><span class="sxs-lookup"><span data-stu-id="f674e-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="f674e-136">它接受 `Credential` 屬性和自動的 `PsDscRunAsCredential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f674e-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="f674e-137">不過，資源只會使用 `Credential` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f674e-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="f674e-138">如需 `PsDscRunAsCredential` 屬性的詳細資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="f674e-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="f674e-139">範例：Group 資源 Credential 屬性</span><span class="sxs-lookup"><span data-stu-id="f674e-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="f674e-140">DSC 在 `Local System` 下執行，所以它已有可變更本機使用者和群組的權限。</span><span class="sxs-lookup"><span data-stu-id="f674e-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="f674e-141">如果新增成員是本機帳戶，就不需要認證。</span><span class="sxs-lookup"><span data-stu-id="f674e-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="f674e-142">如果 `Group` 資源在本機群組中加入網域帳戶，就需要認證。</span><span class="sxs-lookup"><span data-stu-id="f674e-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="f674e-143">Active Directory 不允許匿名查詢。</span><span class="sxs-lookup"><span data-stu-id="f674e-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="f674e-144">`Group` 資源的 `Credential` 屬性是用來查詢 Active Directory 的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="f674e-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="f674e-145">就多數情況而言，這可能是一般的使用者帳戶，因為使用者預設可以*讀取* Active Directory 大部分的物件。</span><span class="sxs-lookup"><span data-stu-id="f674e-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="f674e-146">設定範例</span><span class="sxs-lookup"><span data-stu-id="f674e-146">Example Configuration</span></span>

<span data-ttu-id="f674e-147">以下程式碼範例會使用 DSC 以網域使用者填入本機群組：</span><span class="sxs-lookup"><span data-stu-id="f674e-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="f674e-148">這個程式碼會產生錯誤和警告訊息：</span><span class="sxs-lookup"><span data-stu-id="f674e-148">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="f674e-149">本範例有兩個問題：</span><span class="sxs-lookup"><span data-stu-id="f674e-149">This example has two issues:</span></span>
1. <span data-ttu-id="f674e-150">錯誤說明不建議純文字密碼</span><span class="sxs-lookup"><span data-stu-id="f674e-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="f674e-151">警告建議不要使用網域認證</span><span class="sxs-lookup"><span data-stu-id="f674e-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="f674e-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="f674e-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="f674e-153">第一個錯誤訊息有文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="f674e-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="f674e-154">這個連結說明如何使用 [ConfigurationData](./configData.md) 結構和憑證加密密碼。</span><span class="sxs-lookup"><span data-stu-id="f674e-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="f674e-155">如需憑證和 DSC 的詳細資訊，請[閱讀這篇文章](http://aka.ms/certs4dsc)。</span><span class="sxs-lookup"><span data-stu-id="f674e-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="f674e-156">若要強制施作純文字密碼，資源在設定資料區段中需要有 `PsDscAllowPlainTextPassword` 關鍵字，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f674e-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="f674e-157">`NodeName` 得等同星號，必須有特定的節點名稱。</span><span class="sxs-lookup"><span data-stu-id="f674e-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="f674e-158">**Microsoft 不建議您使用純文字密碼，以免造成嚴重的安全性風險。**</span><span class="sxs-lookup"><span data-stu-id="f674e-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="f674e-159">網域認證</span><span class="sxs-lookup"><span data-stu-id="f674e-159">Domain Credentials</span></span>

<span data-ttu-id="f674e-160">再次執行範例設定指令碼 (加密或不加密)，仍會產生警告，指出不建議使用網域帳戶進行認證。</span><span class="sxs-lookup"><span data-stu-id="f674e-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="f674e-161">使用本機帳戶可降低暴露其他伺服器也可使用之網域認證的可能性。</span><span class="sxs-lookup"><span data-stu-id="f674e-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="f674e-162">**認證搭配 DSC 資源使用時，請盡可能使用本機帳戶，而不用網域帳戶。**</span><span class="sxs-lookup"><span data-stu-id="f674e-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="f674e-163">如果憑證的 `Username` 屬性中有 '\' 或 '@'，DSC 會將其視為網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="f674e-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="f674e-164">使用者名稱的網域部分為 "localhost"、"127.0.0.1" 和 "::1" 時例外。</span><span class="sxs-lookup"><span data-stu-id="f674e-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="f674e-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="f674e-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="f674e-166">在上述的 DSC `Group` 資源範例中，查詢 Active Directory 網域*需要*網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="f674e-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="f674e-167">發生這種情況時，請將 `PSDscAllowDomainUser` 屬性加入 `ConfigurationData` 區塊中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f674e-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="f674e-168">現在設定指令碼產生的 MOF 檔案不再有任何錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="f674e-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
