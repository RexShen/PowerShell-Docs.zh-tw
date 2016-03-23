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
| GroupName| 指出您要確保其特定狀態的群組名稱。| 
| 認證| 表示存取遠端資源所需的認證。 **注意**：此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶加入群組；否則會發生錯誤。
| 描述| 指出群組的描述。| 
| Ensure| 指出群組是否存在。 設定此屬性為 "Absent" 以確保群組不存在。 設定此群組為 "Present" (預設值)，可確保此群組存在。| 
| 成員| 指出您想要確保這些成員會形成群組。| 
| MembersToExclude| 指出您想要確認的使用者不是此群組的成員。| 
| MembersToInclude| 指出您想要確認的使用者是此群組的成員。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例示範如何確定稱為 TestGroup 的群組不存在。 

```powershell
Group GroupExample
{
    # This will remove TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
<!--HONumber=Feb16_HO4-->
