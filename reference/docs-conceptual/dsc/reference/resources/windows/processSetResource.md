---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC ProcessSet 資源
ms.openlocfilehash: b96c6e6830a53d93cf8144cba28e264e23912306
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463987"
---
# <a name="dsc-processset-resource"></a>DSC ProcessSet 資源

> 適用於：Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **ProcessSet** 資源提供了在目標節點設定程序的機制。

## <a name="syntax"></a>語法

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|Path |處理程序可執行檔的路徑。 如果這些是可執行檔的檔案名稱 (不是完整路徑)，則 DSC 資源會搜尋環境 `$env:Path` 變數來尋找檔案。 如果這個屬性的值是完整路徑，則 DSC 不會使用 `$env:Path` 環境變數來尋找檔案，但若任一路徑不存在則會擲回錯誤。 不允許相對路徑。 |
|認證 |表示啟動處理程序的認證。 |
|StandardErrorPath |處理程序要寫入標準錯誤的路徑。 此處的所有檔案都會被覆寫。 |
|StandardInputPath |處理程序從中接收標準輸入的資料流。 |
|StandardOutputPath |處理程序要寫入標準輸出的檔案路徑。 此處的所有檔案都會被覆寫。 |
|WorkingDirectory |用為處理程序目前工作目錄的位置。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定處理程序是否存在。 將此屬性設定為 **Present** 以確保處理程序存在。 否則，請設定為 **Absent**。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。
