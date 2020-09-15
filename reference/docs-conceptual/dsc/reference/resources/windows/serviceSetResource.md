---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC ServiceSet 資源
ms.openlocfilehash: b51cfa86aa6d2114553a0eee681cb88ea93e213f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464395"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **ServiceSet** 資源提供了管理目標節點服務的機制。 此資源是為 **Name** 屬性中所指定每項服務呼叫 [Service 資源](serviceResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。

當您想要將多項服務設定成相同的狀態，請使用此資源。

## <a name="syntax"></a>語法

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |表示服務名稱。 請注意，有時候和顯示名稱不同。 您可以使用 `Get-Service` Cmdlet 取得服務清單及其目前狀態。 |
|StartupType |表示服務的啟動類型。 這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**。 |
|BuiltInAccount |表示用於服務的登入帳戶。 這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。 |
|State |表示您要確保的服務狀態：**Stopped** 或 **Running**。 |
|認證 |表示執行服務資源的帳戶認證。 這個屬性與 **BuiltinAccount** 屬性不能同時使用。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示系統上是否有服務。 請將此屬性設為 **Absent** 以確保服務不存在。 屬性設定為 **Present**，可確保目標服務存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

下列設定會啟動「Windows 音訊」和「遠端桌面服務」服務。

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
