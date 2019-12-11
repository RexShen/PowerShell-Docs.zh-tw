---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
description: 提供在目標節點管理本機群組的機制。
title: DSC GroupSet 資源
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953175"
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet 資源

> 適用於：Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **GroupSet** 資源會提供一個機制，在目標節點管理本機群組。 此資源是為 `GroupName` 參數中指定的每個群組呼叫 [Group 資源](groupResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。

當您想要新增及 (或) 移除多個群組的相同成員清單、移除多個群組，或新增具有相同成員清單的多個群組時，請使用此資源。

## <a name="syntax"></a>語法

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Properties

|屬性 |描述 |
|---|---|
|GroupName |您要確保其特定狀態的群組名稱。 |
|成員 |您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。 這個屬性值為字串陣列，格式為 `Domain\UserName`。 如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。 這樣會產生錯誤。 |
|描述 |群組的描述。 |
|MembersToInclude |使用這個屬性將成員新增至群組的現有成員資格。 這個屬性值為字串陣列，格式為 `Domain\UserName`。 如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。 這樣會產生錯誤。 |
|MembersToExclude |使用這個屬性從現有的群組成員資格移除成員。 這個屬性值為字串陣列，格式為 `Domain\UserName`。 如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。 這樣會產生錯誤。 |
|認證 |存取遠端資源時所需的認證。 此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶新增至群組；否則會發生錯誤。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示群組是否存在。 將此屬性設定為 **Absent** 以確保群組不存在。 設定此群組為 **Present** 以確保群組存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example-1-ensuring-groups-are-present"></a>範例 1：確保群組存在

下例示範如何確保 "myGroup" 和 "myOtherGroup" 兩個群組會出現。

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> 為求簡潔，本範例使用純文字認證。 如需如何在設定 MOF 檔案中加密認證的相關資訊，請參閱[保護 MOF 檔案](../../../pull-server/secureMOF.md)。