---
title:   DSC for Linux nxGroup 資源
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# DSC for Linux nxGroup 資源

PowerShell 預期狀態設定 (DSC) 的 **nxGroup** 資源會提供一個機制，在 Linux 節點管理本機群組。

## 語法

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## [內容]

|  屬性 |  描述 | 
|---|---|
| GroupName| 指出您要確保其特定狀態的群組名稱。| 
| Ensure| 決定是否要檢查群組存在。 將此屬性設定為 "Present" 以確保群組存在。 設為 "Absent" 以確保此群組不存在。 預設值為 "Present"。| 
| 成員| 指定組成群組的成員。| 
| MembersToInclude| 指定您想要確認的使用者是此群組的成員。| 
| MembersToExclude| 指定您想要確認的使用者不是此群組的成員。| 
| PreferredGroupID| 如果可能的話，將群組識別碼設定為提供的值。 如果群組識別碼目前正在使用中，就會使用下一個可用的群組識別碼。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例會確保使用者 “monuser” 存在，而且是 "DBusers" 群組的成員。

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```



<!--HONumber=May16_HO3-->


