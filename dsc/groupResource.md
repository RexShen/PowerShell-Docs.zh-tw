---
title: "DSC 群組資源"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: f6e33f82f495a89a4aa28c64b7974c170d50cfe1
ms.openlocfilehash: 446c9036989c47c03664d978a1dea4e0234ada8d

---

# DSC 群組資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的群組資源會提供一個機制，在目標節點管理本機群組。

##語法##
```
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| GroupName| 您要確保其特定狀態的群組名稱。| 
| 認證| 存取遠端資源時所需的認證。 **注意**：此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶加入群組；否則會發生錯誤。
| 描述| 群組的描述。| 
| Ensure| 指出群組是否存在。 設定此屬性為 "Absent" 以確保群組不存在。 設定此群組為 "Present" (預設值)，可確保此群組存在。| 
| 成員| 您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。 這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。 如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。 這樣會產生錯誤。| 
| MembersToExclude| 使用這個屬性從群組的現有成員資格移除成員。 這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。 如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。 這樣會產生錯誤。| 
| MembersToInclude| 使用這個屬性將成員新增至群組的現有成員資格。 這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。 如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。 這樣會產生錯誤。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例 1

下列範例示範如何確定名為 "TestGroup" 的群組不存在。 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## 範例 2
下列範例顯示如何將 Active Directory 使用者以多電腦實驗室組建 (已經在其內使用本機系統管理員帳戶的 PSCredential) 的一部分，加入本機系統管理員群組。 在網域升級之後，其也會用於網域系統管理員帳戶，然後我們需要將此現有的 PSCredential 轉換為網域能記住的認證，我們如此才可將網域使用者加入成員伺服器上的本機系統管理員群組。

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
     @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'   
      }    
    )
}
                  
$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```




<!--HONumber=Jun16_HO4-->


