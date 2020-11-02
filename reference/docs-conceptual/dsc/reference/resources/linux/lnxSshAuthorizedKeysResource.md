---
ms.date: 07/17/2020
ms.topic: reference
title: DSC for Linux nxSshAuthorizedKeys 資源
description: DSC for Linux nxSshAuthorizedKeys 資源
ms.openlocfilehash: 881e94aa583a745cdac7f01b6e445352ef4ca937
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662754"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>DSC for Linux nxSshAuthorizedKeys 資源

PowerShell 預期狀態設定 (DSC) 的 **nxAuthorizedKeys** 資源會提供一個機制，管理指定使用者的授權 SSH 金鑰。

## <a name="syntax"></a>語法

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|KeyComment |金鑰的唯一註解。 這用來唯一識別金鑰。 |
|使用者名稱 |要為其管理 SSH 授權金鑰的使用者名稱。 如果未定義，則預設使用者為 **root** 。 |
|Key |金鑰的內容。 如果 **Ensure** 設定為 **Present** ，則此項目為必要。|

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定是否已定義金鑰。 將此屬性設定為 **Absent** 以確保索引鍵不存在於使用者的授權金鑰檔案中。 將其設定為 **Present** ，以確保使用者的授權金鑰檔中定義了金鑰。 |

## <a name="example"></a>範例

下列範例會定義使用者 "monuser" 的公用 SSH 授權金鑰。

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```
