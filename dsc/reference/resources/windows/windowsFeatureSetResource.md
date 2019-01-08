---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC WindowsFeatureSet 資源
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047122"
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet 資源

> 適用於：Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeatureSet** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。
此資源是為 `Name` 屬性中指定的每項功能呼叫 [WindowsFeature 資源](windowsfeatureResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。

當您想要將多個 Windows 功能設定成相同的狀態，請使用此資源。

## <a name="syntax"></a>語法

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Properties

|  屬性  |  描述   |
|---|---|
| 名稱| 您想要確保新增或移除的角色或功能名稱。 這與 [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) Cmdlet 的 **Name** 屬性相同，且不是角色或功能的顯示名稱。|
| 認證| 用以新增或移除角色或功能的認證。|
| Ensure| 表示是否已新增角色或功能。 若要確保新增角色或功能，這個屬性請設為 "Present"。若要確保移除角色或功能，請將屬性設定為 "Absent"。|
| IncludeAllSubFeature| 這個屬性設為 **$true** 可讓您使用以 **Name** 屬性指定的功能包含所有必要的子功能。|
| LogPath| 要讓資源提供者記錄作業的記錄檔路徑。|
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。|
| 來源| 如有必要，表示用於安裝的來源檔案位置。|

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
