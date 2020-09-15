---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 使用者資源
ms.openlocfilehash: 340fce45a2074930ae14ca1aaeef7eff78531916
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463766"
---
# <a name="dsc-user-resource"></a>DSC 使用者資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **User** 資源，會提供在目標節點管理本機使用者帳戶的機制。

## <a name="syntax"></a>語法

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|UserName |指出您要確保其特定狀態的帳戶名稱。 |
|描述 |表示您要使用的使用者帳戶描述。 |
|已停用 |表示帳戶是否啟用。 將此屬性設定為 `$true` 以確保此帳戶已停用，而將它設定為 `$false` 可確定它已啟用。 |
|FullName |代表有您要使用的完整使用者帳戶名稱的字串。 |
|密碼 |表示您想要用於這個帳戶的密碼。 |
|PasswordChangeNotAllowed |表示使用者是否可以變更密碼。 將此屬性設定為 `$true` 以確保使用者無法變更密碼，而將它設定為 `$false` 可允許使用者變更密碼。 預設值是 `$false`。 |
|PasswordChangeRequired |表示使用者是否必須在下次登入時變更密碼。 如果使用者必須變更密碼，請將此屬性設定為 `$true`。 預設值是 `$true`。 |
|PasswordNeverExpires |表示密碼是否會到期。 為確保這個帳戶的密碼永遠不會到期，請將這個屬性設定為 `$true`。 如果密碼會到期，則將其設定為 `$false`。 預設值是 `$false`。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示帳戶是否存在。 將此屬性設定為 **Present** 以確保帳戶存在，而設定為 **Absent** 可確保帳戶不存在。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```
