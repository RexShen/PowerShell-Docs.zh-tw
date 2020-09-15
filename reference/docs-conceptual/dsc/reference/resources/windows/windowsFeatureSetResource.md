---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC WindowsFeatureSet 資源
ms.openlocfilehash: 856c56e0b35a26add729ef77db9dca71fdc0a4d0
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463851"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet 資源

> 適用於：Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeatureSet** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。 此資源是為 **Name** 屬性中所指定每項功能呼叫 [WindowsFeature 資源](windowsfeatureResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。

當您想要將多個 Windows 功能設定成相同的狀態，請使用此資源。

## <a name="syntax"></a>語法

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|  屬性  |  描述   |
|---|---|
|名稱 |您想要確保新增或移除的角色或功能名稱。 這與 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) Cmdlet 的 **Name** 屬性相同，且不是角色或功能的顯示名稱。 |
|來源 |如有必要，表示用於安裝的來源檔案位置。 |
|IncludeAllSubFeature |這個屬性設定為 `$true` 可讓您使用以 **Name** 屬性指定的功能包含所有必要子功能。 |
|認證 |用以新增或移除角色或功能的認證。 |
|LogPath |要讓資源提供者記錄作業的記錄檔路徑。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示是否已新增角色或功能。 若要確保新增角色或功能，請將此屬性設定為 **Present**。 若要確保移除角色或功能，請將此屬性設定為 **Absent**。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

下列設定可確保安裝 **Web 伺服器** (IIS) 和 **SMTP 伺服器**功能及其各自的所有子功能。

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
