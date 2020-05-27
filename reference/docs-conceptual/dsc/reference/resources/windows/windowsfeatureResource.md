---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WindowsFeature 資源
ms.openlocfilehash: 7f9b200b4d10aef6c8a3f76c497f4d60e8062cb5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557392"
---
# <a name="dsc-windowsfeature-resource"></a>DSC WindowsFeature 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeature** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。

## <a name="syntax"></a>語法

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |表示您想要確保新增或移除的角色或功能名稱。 這與來自 **Get-WindowsFeature** Cmdlet 的 [Name](/powershell/module/servermanager/Get-WindowsFeature) 屬性相同，不是角色或功能的顯示名稱。 |
|認證 |表示要用以新增或移除角色或功能的認證。 |
|IncludeAllSubFeature |將此屬性設定為 `$true` 可讓您使用以 **Name** 屬性指定的功能狀態，來確保所有必要子功能的狀態。 |
|LogPath |表示要讓資源提供者記錄作業的記錄檔路徑。 |
|來源 |如有必要，表示用於安裝的來源檔案位置。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示角色或功能是否新增。 若要確保新增角色或功能，請將此屬性設定為 **Present**。 若要確保移除角色或功能，請將此屬性設定為 **Absent**。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
