---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 登錄資源
ms.openlocfilehash: 8819b3704fa1a61d2be5ce11c974542f48177e09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188695"
---
# <a name="dsc-registry-resource"></a>DSC 登錄資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

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
|  屬性  |  描述   |
|---|---|
| 按鍵| 指出您要確保其特定狀態的登錄機碼路徑。 此路徑必須包含登錄區。|
| ValueName| 指出登錄值的名稱。 若要新增或移除登錄機碼，請將此屬性指定為空字串，且不指定 ValueType 或 ValueData。 若要修改或移除登錄機碼的預設值，請將此屬性指定為空字串，同時也指定 ValueType 或 ValueData。|
| Ensure| 指出金鑰和值是否存在。 若要確定存在，可將此屬性設定為 "Present"。 若要確定不存在，可將此屬性設定為 "Absent"。 預設值為 "Present"。|
| Force| 如果指定的登錄機碼存在，__Force__ 會以新值覆寫登錄機碼。 如果要刪除含有子機碼的登錄機碼，這必須是 __$true__|
| Hex| 指出資料是否以十六進位格式表示。 如果指定為 Hex，則 DWORD/QWORD 值資料會以十六進位格式顯示。 不適用於其他類型。 預設值為 __$false__。|
| DependsOn| 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。|
| ValueData| 登錄值的資料。|
| ValueType| 指出值的類型。 支援的類型包括：
<ul><li>字串 (REG_SZ)</li>


<li>二進位 (REG-BINARY)</li>


<li>Dword 32 位元 (REG_DWORD)</li>


<li>Qword 64 位元 (REG_QWORD)</li>


<li>多字串 (REG_MULTI_SZ)</li>


<li>可擴充的字串 (REG_EXPAND_SZ)</li></ul>

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

>**注意︰** 變更 **HKEY\_CURRENT\_USER** 中的登錄設定必須以使用者認證執行設定，而不是使用系統。
>您可以使用 **PsDscRunAsCredential** 屬性指定設定時所要使用的使用者認證。 如需範例，請參閱＜[使用使用者認證執行 DSC](runAsUser.md)＞
