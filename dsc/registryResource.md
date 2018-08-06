---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 登錄資源
ms.openlocfilehash: 8d74473d167b70182c3a16c1d39d2a9e797afb1b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267716"
---
# <a name="dsc-registry-resource"></a>DSC 登錄資源

_適用於：Windows PowerShell 4.0、Windows PowerShell 5.0_

Windows PowerShell 預期狀態設定 (DSC) 的 **Registry** 資源會提供一個機制，在目標節點管理登錄機碼和值。

## <a name="syntax"></a>語法

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Properties

| 屬性 | 描述 |
| --- | --- |
| 按鍵| 指出您要確保其特定狀態的登錄機碼路徑。 此路徑必須包含登錄區。|
| ValueName| 指出登錄值的名稱。 若要新增或移除登錄機碼，請將此屬性指定為空字串，且不指定 ValueType 或 ValueData。 若要修改或移除登錄機碼的預設值，請將此屬性指定為空字串，同時也指定 ValueType 或 ValueData。|
| Ensure| 指出金鑰和值是否存在。 若要確定存在，可將此屬性設定為 "Present"。 若要確定不存在，可將此屬性設定為 "Absent"。 預設值為 "Present"。|
| Force| 如果指定的登錄機碼存在，**Force** 會以新值覆寫登錄機碼。 如果要刪除含有子機碼的登錄機碼，這必須是 **$true** |
| Hex| 指出資料是否以十六進位格式表示。 如果指定為 Hex，則 DWORD/QWORD 值資料會以十六進位格式顯示。 不適用於其他類型。 預設值為 **$false**。|
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。|
| ValueData| 登錄值的資料。|
| ValueType| 指出值的類型。 支援的型別包括：字串 (REG_SZ)、二進位 (REG-BINARY)、Dword 32 位元 (REG_DWORD)、Qword 64 位元 (REG_QWORD)、多字串 (REG_MULTI_SZ)、可擴充的字串 (REG_EXPAND_SZ) |

## <a name="example"></a>範例

此範例可確保 **HKEY\_LOCAL\_MACHINE** 登錄區包含名為"ExampleKey"的索引鍵。

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> 變更 `HKEY\CURRENT\USER` 登錄區中的登錄設定必須以使用者認證執行設定，而不是使用系統認證。 您可以使用 **PsDscRunAsCredential** 屬性指定設定時所要使用的使用者認證。 如需範例，請參閱[以使用者認證執行 DSC](runAsUser.md)。