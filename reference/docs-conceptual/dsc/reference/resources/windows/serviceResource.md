---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC Service 資源
ms.openlocfilehash: f936f58ffd00f84d8c6d5d41d93378eaa8db5879
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463579"
---
# <a name="dsc-service-resource"></a>DSC Service 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **Service** 資源提供了管理目標節點服務的機制。

## <a name="syntax"></a>語法

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |表示服務名稱。 請注意，有時候和顯示名稱不同。 您可以使用 `Get-Service` Cmdlet 取得服務清單及其目前狀態。 |
|BuiltInAccount |表示用於服務的登入帳戶。 這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。 |
|認證 |表示執行服務的帳戶認證。 這個屬性與 **BuiltinAccount** 屬性不能同時使用。 |
|StartupTimeout | 等待服務執行的毫秒數。|
|StartupType |表示服務的啟動類型。 這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**。 |
|State |表示您要確保的服務狀態。 值如下：**Running** 或 **Stopped**。 |
|TerminateTimeout |等待服務停止的毫秒數。|
|相依性 | 服務應具備的相依性名稱陣列。 |
|描述 |表示目標服務的描述。 |
|DesktopInteract | 指出服務是否應能夠和桌面上的視窗通訊。 針對不是以 LocalSystem 執行的服務，必須為 false。|
|DisplayName |表示目標服務的顯示名稱。 |
|路徑 |表示新服務的二進位檔路徑。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示系統上是否有目標服務。 請將此屬性設定為**Absent** 以確保目標服務不存在。 屬性設定為 **Present**，可確保目標服務存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
