---
title: "DSC for Linux nxSshAuthorizedKeys 資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: edc906b4e9c925320c4ed00c5ab295189066ccb9

---

# DSC for Linux nxSshAuthorizedKeys 資源

PowerShell 預期狀態設定 (DSC) 的 **nxAuthorizedKeys** 資源會提供一個機制，管理指定使用者的授權 SSH 金鑰。

## 語法

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## [內容]

|  屬性 |  描述 | 
|---|---|
| KeyComment| 金鑰的唯一註解。 這用來唯一識別金鑰。| 
| Ensure| 指定是否已定義金鑰。 設定此屬性為 "Absent" 以確保索引鍵不存在於使用者的授權金鑰檔案。 設定為 "Present"，以確保使用者的授權金鑰檔中定義了金鑰。| 
| Username| 要為其管理 SSH 授權金鑰的使用者名稱。 如果未定義，則預設使用者為 "root"。| 
| 按鍵| 金鑰的內容。 如果 **Ensure** 設為 "Present"，則必須有此項。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例會定義使用者 "monuser" 的公用 SSH 授權金鑰。

```
Import-DSCResource -Module nx 

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
} 
}
```




<!--HONumber=Jun16_HO4-->


