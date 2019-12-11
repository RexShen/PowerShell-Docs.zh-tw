---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC 群組資源
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954655"
---
# <a name="dsc-group-resource"></a>DSC 群組資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 的**群組**資源會提供一個機制，在目標節點管理本機群組。

## <a name="syntax"></a>語法

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Properties

|屬性 |描述 |
|---|---|
|GroupName |您要確保其特定狀態的群組名稱。 |
|認證 |存取遠端資源時所需的認證。 此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶新增至群組；否則，在目標節點上執行設定時會發生錯誤。
|描述 |群組的描述。 |
|成員 |您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。 這個屬性值為字串陣列，格式為 `Domain\UserName`。 如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。 這麼做會產生錯誤。 |
|MembersToExclude |使用這個屬性從群組的現有成員資格移除成員。 這個屬性值為字串陣列，格式為 `Domain\UserName`。 如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。 這麼做會產生錯誤。 |
|MembersToInclude |使用這個屬性將成員新增至群組的現有成員資格。 這個屬性值為字串陣列，格式為 `Domain\UserName`。 如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。 這樣會產生錯誤。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指出群組是否存在。 將此屬性設定為 **Absent** 以確保群組不存在。 設定此群組為 **Present** 以確保此群組存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example-1-ensure-group-is-not-present"></a>範例 1：確定群組不存在

下列範例示範如何確定名為 "TestGroup" 的群組不存在。

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a>範例 2：將網域使用者新增至本機群組

下列範例顯示如何將 Active Directory 使用者新增至本機系統管理員群組，成為已使用本機系統管理員帳戶 PSCredential 之多電腦實驗室組建的一部分。 因為這也會用於網域系統管理員帳戶 (在網域升級之後)，所以我們需要將此現有的 PSCredential 轉換為適用於網域的認證。 之後，我們便可將網域使用者新增到成員伺服器上的本機系統管理員群組。

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>範例 3

下列範例示範如何確定伺服器 TigerTeamSource.Contoso.Com 上的本機群組 TigerTeamAdmins 不包含特定的網域帳戶 Contoso\JerryG。

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```