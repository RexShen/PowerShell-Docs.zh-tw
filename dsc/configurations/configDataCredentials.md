---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定資料的認證選項
ms.openlocfilehash: 660c3643f7eb2e9ccb91bd992747fb9d5da0ccdb
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323293"
---
# <a name="credentials-options-in-configuration-data"></a>設定資料的認證選項

>適用於：Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>純文字密碼和網域使用者

包含未加密認證的 DSC 設定會產生有關純文字密碼的錯誤訊息。
DSC 也會在使用網域認證時產生警告。
若要隱藏這些錯誤和警告訊息，請使用 DSC 設定資料關鍵字：

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> 儲存/傳輸未加密的純文字密碼通常是不安全的。 建議您使用本主題稍後所涵蓋的技術來保護認證。
> Azure Automation DSC 服務能讓您集中管理及安全儲存要在設定中編譯的認證。
> 如需詳細資訊，請參閱：[編譯 DSC 設定 / 認證資產](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>處理 DSC 的認證

DSC 設定資源預設執行為 `Local System`。
不過，有些資源需要認證，例如當 `Package` 資源需要在特定使用者帳戶下安裝軟體時。

資源過去使用硬式編碼的 `Credential` 屬性名稱來處理這種情形。
WMF 5.0 為所有資源加入了自動的 `PsDscRunAsCredential` 屬性。
如需關於使用 `PsDscRunAsCredential` 的相關資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。
較新的資源和自訂的資源可以使用這個自動屬性，不用建立自己專有的認證屬性。

> [!NOTE]
> 某些資源的目的是為特定原因使用多個認證，所以會有自己的認證屬性。

若要在資源上尋找可用的認證屬性，請使用 `Get-DscResource -Name ResourceName -Syntax` 或 ISE 的 Intellisense (`CTRL+SPACE`)。

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

本例使用 `PSDesiredStateConfiguration` 內建 DSC 資源模組的 [Group](../resources/resources.md) 資源。
它會建立本機群組並新增或移除成員。
它接受 `Credential` 屬性和自動的 `PsDscRunAsCredential` 屬性。
不過，資源只會使用 `Credential` 屬性。

如需 `PsDscRunAsCredential` 屬性的詳細資訊，請參閱[以使用者認證執行 DSC](runAsUser.md)。

## <a name="example-the-group-resource-credential-property"></a>範例：群組資源認證屬性

DSC 在 `Local System` 下執行，所以它已有可變更本機使用者和群組的權限。
如果新增成員是本機帳戶，就不需要認證。
如果 `Group` 資源在本機群組中加入網域帳戶，就需要認證。

Active Directory 不允許匿名查詢。
`Group` 資源的 `Credential` 屬性是用來查詢 Active Directory 的網域帳戶。
就多數情況而言，這可能是一般的使用者帳戶，因為使用者預設可以*讀取* Active Directory 大部分的物件。

## <a name="example-configuration"></a>設定範例

以下程式碼範例會使用 DSC 以網域使用者填入本機群組：

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

這個程式碼會產生錯誤和警告訊息：

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

本範例有兩個問題：

1. 錯誤說明不建議純文字密碼
2. 警告建議不要使用網域認證

旗標 **PSDSCAllowPlainTextPassword** 和 **PSDSCAllowDomainUser** 會隱藏錯誤和警告，通知使用者所涉及的風險。

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

第一個錯誤訊息有文件的 URL。
這個連結說明如何使用 [ConfigurationData](./configData.md) 結構和憑證加密密碼。
如需憑證和 DSC 的詳細資訊，請[閱讀這篇文章](https://aka.ms/certs4dsc)。

若要強制施作純文字密碼，資源在設定資料區段中需要有 `PsDscAllowPlainTextPassword` 關鍵字，如下所示：

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

### <a name="localhostmof"></a>localhost.mof

**PSDSCAllowPlainTextPassword** 旗標會要求使用者確認將純文字密碼儲存在 MOF 檔案中的風險。 在產生的 MOF 檔案中，即使使用包含 **SecureString** 的 **PSCredential** 物件，密碼仍然會顯示為純文字。 這是公開認證的唯一時間。 取得對此 MOF 檔案的存取權限，可讓任何人存取系統管理員帳戶。

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

### <a name="credentials-in-transit-and-at-rest"></a>傳輸中和待用的認證

- **PSDscAllowPlainTextPassword** 旗標允許編譯包含純文字密碼的 MOF 檔案。
  儲存包含純文字密碼的 MOF 檔案時，請採取預防措施。
- 當 MOF 檔案以**推送**模式傳送到節點時，WinRM 會加密通訊以保護純文字密碼，除非您使用 **AllowUnencrypted** 參數覆寫預設值。
  - 使用憑證加密 MOF，可以在 MOF 檔案套用到節點之前保護待用檔案。
- 在**提取**模式中，您可以將 Windows 提取伺服器設定為使用 HTTPS，以使用 Internet Information Server 中所指定的通訊協定來加密流量。 如需詳細資訊，請參閱[設定 DSC 提取用戶端](../pull-server/pullclient.md)和[使用憑證保護 MOF 檔案](../pull-server/secureMOF.md)文章。
  - 在 [Azure 自動化狀態設定](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) \(機器翻譯\) 服務中，提取流量一律會加密。
- 在節點上，MOF 檔案在待用時加密 (從 PowerShell 5.0 開始)。
  - 在 PowerShell 4.0 中，MOF 檔案在待用時是未加密的，除非它們在推送或提取至節點時使用憑證加密。

**Microsoft 不建議您使用純文字密碼，以免造成嚴重的安全性風險。**

## <a name="domain-credentials"></a>網域認證

再次執行範例設定指令碼 (加密或不加密)，仍會產生警告，指出不建議使用網域帳戶進行認證。
使用本機帳戶可降低暴露其他伺服器也可使用之網域認證的可能性。

**認證搭配 DSC 資源使用時，請盡可能使用本機帳戶，而不用網域帳戶。**

若認證的 `Username` 屬性中有 '\\' 或 '\@'，則 DSC 會將它視為網域帳戶。
使用者名稱的網域部分為 "localhost"、"127.0.0.1" 和 "::1" 時例外。

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

在上述的 DSC `Group` 資源範例中，查詢 Active Directory 網域*需要*網域帳戶。
發生這種情況時，請將 `PSDscAllowDomainUser` 屬性加入 `ConfigurationData` 區塊中，如下所示：

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

現在設定指令碼產生的 MOF 檔案不再有任何錯誤或警告。
