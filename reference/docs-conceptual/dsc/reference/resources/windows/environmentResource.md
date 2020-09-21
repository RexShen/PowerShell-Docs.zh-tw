---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 環境資源
ms.openlocfilehash: d8519a66d457767dcbc0e08b01a69a9264997479
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464412"
---
# <a name="dsc-environment-resource"></a>DSC 環境資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的**環境**資源會提供管理系統環境變數的機制。

## <a name="syntax"></a>語法

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |指出您要確保其特定狀態的環境變數名稱。 |
|Path |定義設定中的環境變數。 如果變數是 **Path** 變數，請將這個屬性設定為 `$true`；否則請設定為 `$false`。 預設值為 `$false`。 如果要設定的變數是 **Path** 變數，則透過 **Value** 屬性提供的值就會附加至現有的值。 |
|目標| 指出擷取變數的位置：電腦或處理序。 若同時指定兩者，則只會傳回來自電腦的值。 預設為兩者，因為這是資源其餘部分的預設。 |
|值 |要指派給環境變數的值。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指出變數是否存在。 如果沒有環境變數，請將這個屬性設為 **Present** 以建立環境變數；或如果已有變數，則確保其值符合透過 **Value** 屬性所提供的值。 如果有變數，將它設為 **Absent** 可刪除變數。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

下例確保 TestEnvironmentVariable 存在，且有值 _TestValue_。 如果不存在，就會建立它。

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
