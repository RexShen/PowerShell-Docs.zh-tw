---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC WindowsOptionalFeatureSet 資源
ms.openlocfilehash: e4f88f1cae6d7ddb3596ab4f27eb3766259f1a31
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464157"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet 資源

> 適用於：Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeatureSet** 資源提供一個機制，確保可在目標節點上啟用選用功能。 此資源是針對**Name** 屬性中所指定每項功能呼叫 [WindowsOptionalFeature 資源](windowsOptionalFeatureResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。

當您想要將多個 Windows 選用功能設定成相同的狀態，請使用此資源。

## <a name="syntax"></a>語法

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
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
|LogLevel |記錄中顯示的最大輸出等級。 接受的值為：**ErrorsOnly**、**ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation**。 |
|LogPath |要讓資源提供者記錄作業的記錄檔路徑。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指定是否啟用功能。 若要確保已啟用此功能，請將此屬性設定為 **Enable**。 若要確保已停用此功能，請將此屬性設定為 **Disable**。 預設值為 **Enable**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。
