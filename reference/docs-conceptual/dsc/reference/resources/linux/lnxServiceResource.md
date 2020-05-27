---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxService 資源
ms.openlocfilehash: 30f3b15fccd1491fac2989832486ad15d062c1ad
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563977"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC for Linux nxService 資源

PowerShell 預期狀態設定 (DSC) 的 **nxService** 資源會提供一個機制，在 Linux 節點管理服務。

## <a name="syntax"></a>語法

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |要設定的服務/精靈名稱。 |
|控制器 |設定服務時所要使用的服務控制站類型。 |
|啟用 |指出是否在開機時啟動服務。 |
|State |表示服務是否正在執行。 將此屬性設定為 **Stopped**，以確保服務未正在執行中。 將其設定為 **Running**，以確保服務未正在執行中。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |

## <a name="additional-information"></a>其他資訊

如果服務定義或服務的指令碼不存在，**nxService** 資源將不會建立服務定義或服務的指令碼。 您可以使用 PowerShell 預期狀態設定 **nxFile** 資源資源，以管理服務定義檔或指令碼的內容是否存在。

## <a name="example"></a>範例

下列範例顯示 'httpd' 服務設定 (適用於 Apache HTTP Server)，且已向 **SystemD** 服務控制站登錄。

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
