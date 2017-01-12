---
title: "設定資料的認證選項"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 162ae26dec67e8259661bb58c1b713818627220b
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
---
# <a name="credentials-options-in-configuration-data"></a>設定資料的認證選項
>適用於：Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>純文字密碼和網域使用者

包含未加密認證的 DSC 設定會產生有關純文字密碼的錯誤訊息。
DSC 也會在使用網域認證時產生警告。
若要隱藏這些錯誤和警告訊息，請使用 DSC 設定資料關鍵字：
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

>**注意**︰使用純文字密碼並不安全。 建議您使用本主題稍後所涵蓋的技術來保護認證。

傳遞純文字認證的範例如下︰

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
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
      
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>處理 DSC 的認證

DSC 設定資源預設執行為 `Local System`。
不過，有些資源需要認證，例如當 `Package` 資源需要在特定使用者帳戶下安裝軟體時。

資源過去使用硬式編碼的 `Credential` 屬性名稱來處理這種情形。
WMF 5.0 為所有資源加入了自動的 `PsDscRunAsCredential` 屬性。 如需關於使用 `PsDscRunAsCredential` 的相關資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。
較新的資源和自訂的資源可以使用這個自動屬性，不用建立自己專有的認證屬性。

請注意，某些資源的設計是針對特定原因使用多個認證，所以會有自己的認證屬性。

若要在資源上尋找可用的認證屬性，請使用 `Get-DscResource -Name ResourceName -Syntax` 或 ISE 的 Intellisense (`CTRL+SPACE`)。

```PowerShell
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

本例使用 `PSDesiredStateConfiguration` 內建 DSC 資源模組的 [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) 資源。
它會建立本機群組並新增或移除成員。
它接受 `Credential` 屬性和自動的 `PsDscRunAsCredential` 屬性。
不過，資源只會使用 `Credential` 屬性。
請參閱 [WMF 版本資訊](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_runas)以深入了解 `PsDscRunAsCredential`。

## <a name="example-the-group-resource-credential-property"></a>範例：Group 資源 Credential 屬性

DSC 在 `Local System` 下執行，所以它已有可變更本機使用者和群組的權限。
如果新增成員是本機帳戶，就不需要認證。
如果 `Group` 資源在本機群組中加入網域帳戶，就需要認證。

Active Directory 不允許匿名查詢。
`Group` 資源的 `Credential` 屬性是用來查詢 Active Directory 的網域帳戶。
就多數情況而言，這可能是一般的使用者帳戶，因為使用者預設可以*讀取* Active Directory 大部分的物件。

## <a name="example-configuration"></a>設定範例

以下程式碼範例會使用 DSC 以網域使用者填入本機群組：

```PowerShell
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

這個程式碼會產生錯誤和警告訊息：

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

本範例有兩個問題：
1.  錯誤說明不建議純文字密碼
2.  警告建議不要使用網域認證

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

第一個錯誤訊息有文件的 URL。
這個連結說明如何使用 [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) 結構和憑證加密密碼。
如需憑證和 DSC 的詳細資訊，請[閱讀這篇文章](http://aka.ms/certs4dsc)。

若要強制施作純文字密碼，資源在設定資料區段中需要有 `PsDscAllowPlainTextPassword` 關鍵字，如下所示：

```PowerShell
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

*請注意，`NodeName` 不得等同星號，必須有特定的節點名稱。*

**Microsoft 不建議您使用純文字密碼，以免造成嚴重的安全性風險。**

## <a name="domain-credentials"></a>網域認證

再次執行範例設定指令碼 (加密或不加密)，仍會產生警告，指出不建議使用網域帳戶進行認證。
使用本機帳戶可降低暴露其他伺服器也可使用之網域認證的可能性。

**認證搭配 DSC 資源使用時，請盡可能使用本機帳戶，而不用網域帳戶。**

如果憑證的 `Username` 屬性中有 '\' 或 '@'，DSC 會將其視為網域帳戶。
使用者名稱的網域部分為 "localhost"、"127.0.0.1" 和 "::1" 時例外。

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

在上述的 DSC `Group` 資源範例中，查詢 Active Directory 網域*需要*網域帳戶。
發生這種情況時，請將 `PSDscAllowDomainUser` 屬性加入 `ConfigurationData` 區塊中，如下所示：

```PowerShell
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

現在設定指令碼產生的 MOF 檔案不再有任何錯誤或警告。

