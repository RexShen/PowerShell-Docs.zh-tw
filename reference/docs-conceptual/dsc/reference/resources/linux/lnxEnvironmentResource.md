---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxEnvironment 資源
ms.openlocfilehash: 2f673dfbc3b6e93d7e186e4a63b75d16a31b5181
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463681"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC for Linux nxEnvironment 資源

PowerShell 預期狀態設定 (DSC) 的 **nxEnvironment** 資源會提供在 Linux 節點上管理系統環境變數的機制。

## <a name="syntax"></a>語法

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |指出您要確保其特定狀態的環境變數名稱。 |
|值 |要指派給環境變數的值。 |
|Path |定義設定中的環境變數。 如果變數是 **Path** 變數，請將這個屬性設定為 `$true`；否則請設定為 `$false`。 預設值為 `$false`。 如果要設定的變數是 **Path** 變數，則透過 **Value** 屬性提供的值就會附加至現有的值。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |決定是否要檢查變數存在。 將此屬性設定為 **Present** 以確保變數存在。 將其設定為 **Absent** 以確保此變數不存在。 預設值為 **Present**。 |

## <a name="additional-information"></a>其他資訊

- 如果 **Path** 不存在，或設定為 `$false`，則環境變數會在 `/etc/environment` 中受到管理。
  您的程式或指令碼可能需要設定為以 `/etc/environment` 檔為來源，以存取受管理的環境變數。
- 如果 **Path** 設定為 `$true`，則環境變數會在檔案 `/etc/profile.d/DSCenvironment.sh` 中受到管理。 如果不存在，則會建立這個檔案。 如果 **Ensure** 設定成 **Absent**，而 **Path** 設定成 `$true`，則現有的環境變數只會從 `/etc/profile.d/DSCenvironment.sh` 中移除，而不會從其他檔案中移除。

## <a name="example"></a>範例

下列範例示範如何使用 **nxEnvironment** 資源以確保 **TestEnvironmentVariable** 存在且具有值 "Test-Value"。 如果 **TestEnvironmentVariable** 不存在，就會加以建立。

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
