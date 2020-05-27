---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxUser 資源
ms.openlocfilehash: 4cf8080fbfa58e082ed007d42d6aa2648d1cf58a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557170"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC for Linux nxUser 資源

PowerShell 預期狀態設定 (DSC) 的 **nxUser** 資源會提供一個機制，在 Linux 節點管理本機使用者。

## <a name="syntax"></a>語法

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>屬性

|屬性 |指出您要確保其特定狀態的帳戶名稱。 |
|---|---|
|UserName |指定您要確認檔案或目錄狀態的位置。 |
|FullName |字串，包含要用於使用者帳戶的完整名稱。 |
|描述 |使用者帳戶的描述。 |
|密碼 |Linux 電腦適當表單的使用者密碼雜湊。 一般而言，這是「加鹽」過 (在密碼任意固定位置插入特定的字串) 的 SHA-256 或 SHA-512 雜湊。 在 Debian 和 Ubuntu Linux 上，這個值可使用 `mkpasswd` 命令產生。 針對其他 Linux 散發版本，Python Crypt 程式庫的 crypt 方法可用來產生此雜湊。 |
|已停用 |指出此帳戶是否啟用。 將此屬性設定為 `$true` 以確保此帳戶已停用，而將它設定為 `$false` 可確定它已啟用。 |
|PasswordChangeRequired |指出使用者是否可以變更密碼。 將此屬性設定為 `$true` 以確保使用者無法變更密碼，而將它設定為 `$false` 可允許使用者變更密碼。 預設值是 `$false`。 如果之前不存在此使用者帳戶，而且正在建立中，才會評估這個屬性。 |
|HomeDirectory |使用者主目錄。 |
|GroupID |使用者主要群組識別碼。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定帳戶是否存在。 將此屬性設定為 **Present** 以確保帳戶存在，而設定為 **Absent** 可確保帳戶不存在。 |

## <a name="example"></a>範例

下列範例會確保使用者 "monuser" 存在，而且是 "DBusers" 群組的成員。

```powershell
Import-DSCResource -Module nx

Node $node
{
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
