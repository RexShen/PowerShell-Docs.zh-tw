---
ms.date: 08/28/2020
ms.topic: reference
title: DSC WindowsOptionalFeature 資源
description: DSC WindowsOptionalFeature 資源
ms.openlocfilehash: 1c7e888ea49b0d1710cc22c975cb618999238f67
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143053"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC WindowsOptionalFeature 資源

> 適用於：Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeature** 資源提供一個機制，確保可在目標節點上啟用選用功能。

> [!NOTE]
> **WindowsOptionalFeature** 僅適用於 Windows 用戶端電腦，例如 Windows 10。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>語法

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |表示您想要確保啟用或停用的功能名稱。 |
|NoWindowsUpdateCheck |指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。 若為 `$true`，則 DISM 不連絡 WU。 |
|RemoveFilesOnDisable |當 **Ensure** 設定為 **Absent** 時，設定為 `$true` 可移除與此功能建立關聯的所有檔案。 |
|LogLevel |記錄中顯示的最大輸出等級。 接受的值為： **ErrorsOnly** 、 **ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation** 。 |
|LogPath |要讓資源提供者記錄作業的記錄檔路徑。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定是否已啟用此功能。 若要確保已啟用此功能，請將此屬性設定為 _Enable_ 。 若要確保已停用此功能，請將此屬性設定為 _Disable_ 。 預設值為 _Enable_ 。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。
