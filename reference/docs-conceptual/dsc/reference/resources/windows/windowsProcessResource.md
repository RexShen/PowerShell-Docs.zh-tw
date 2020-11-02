---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsProcess 資源
description: DSC WindowsProcess 資源
ms.openlocfilehash: 3076e9cb857b78953c164253351b23e7da9b40c6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143002"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsProcess** 資源提供了在目標節點設定程序的機制。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>語法

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|引數 |表示要保持原狀傳遞至處理程序的引數字串。 如果需要傳遞數個引數，請將它們都放在這個字串裡。 |
|Path |處理程序可執行檔的路徑。 如果這是可執行檔的檔案名稱 (不是完整路徑)，則 DSC 資源會搜尋環境 `$env:Path` 變數來尋找可執行檔。 如果這個屬性的值是完整路徑，DSC 將不會使用 `$env:Path` 變數來尋找檔案，但若路徑不存在則會擲回錯誤。 不允許相對路徑。 |
|認證 |表示啟動處理程序的認證。 |
|StandardErrorPath |表示寫入標準錯誤的目錄路徑。 此處的所有檔案都會被覆寫。 |
|StandardInputPath |表示標準輸入的位置。 |
|StandardOutputPath |表示寫入標準輸出的位置。 此處的所有檔案都會被覆寫。 |
|WorkingDirectory |表示會用為處理程序目前工作目錄的位置。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |表示處理程序是否存在。 將此屬性設定為 **Present** 以確保處理程序存在。 否則，請設定為 **Absent** 。 預設值為 **Present** 。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |
