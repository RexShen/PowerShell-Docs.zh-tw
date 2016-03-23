# DSC for Linux nxUser 資源

PowerShell 預期狀態設定 (DSC) 的 **nxUser** 資源會提供一個機制，在 Linux 節點管理本機使用者。

## 語法

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ Mode = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## [內容]

|  屬性 |  指出您要確保其特定狀態的帳戶名稱。 | 
|---|---|
| UserName| 指定您要確認檔案或目錄狀態的位置。| 
| Ensure| 指定帳戶是否存在。 設定此屬性為 "Present" 以確保帳戶存在，而設為 "Absent" 可確保帳戶不存在。| 
| FullName| 字串，包含要用於使用者帳戶的完整名稱。| 
| 描述| 使用者帳戶的描述。| 
| 密碼| Linux 電腦適當表單的使用者密碼雜湊。 一般而言，這是「加鹽」過 (在密碼任意固定位置插入特定的字串) 的 SHA-256 或 SHA-512 雜湊。 在 Debian 和 Ubuntu Linux 上，這個值可使用 mkpasswd 命令產生。 針對其他 Linux 散發版本，Python 的 Crypt 程式庫的 crypt 方法可用來產生此雜湊。| 
| 停用| 指出此帳戶是否啟用。 將此屬性設定為 **$true** 以確保此帳戶已停用，而設定為 **$false** 可確定已啟用。| 
| PasswordChangeRequired| 指出使用者是否可以變更密碼。 將此屬性設定為 **$true** 以確保使用者無法變更密碼，而設定為 **$false** 可允許使用者變更密碼。 預設值為 **$false**。 如果之前不存在此使用者帳戶，而且正在建立中，才會評估這個屬性。| 
| HomeDirectory| 使用者主目錄。| 
| GroupID| 使用者主要群組識別碼。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 "ResourceName"，而它的類型是 "ResourceType"，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 範例

下列範例會確保使用者 "monuser" 存在，而且是 "DBusers" 群組的成員。

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
<!--HONumber=Feb16_HO4-->
