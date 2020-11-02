---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsPackageCab 資源
description: DSC WindowsPackageCab 資源
ms.openlocfilehash: 3ac10eb2a7da502b8cac23ab8bfee869a4e26fd3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143019"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab 資源

> 適用於：Windows PowerShell 5.1

Windows PowerShell 預期狀態設定 (DSC) 中的 **WindowsPackageCab** 資源提供一個機制，可在目標節點上安裝或解除安裝 Windows 封包 (.cab) 套件。

目標節點上必須安裝 DISM PowerShell 模組。 如需相關資訊，請參閱[在 Windows PowerShell 中使用 DISM](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)。

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>語法

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |指出您想要確保其特定狀態的套件名稱。 |
|SourcePath |指出套件所在的檔案路徑 |
|LogPath |指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指出是否要安裝此套件。 將此屬性設定為 **Absent** 以確保不會安裝此套件 (或如果已安裝，請解除安裝此套件)。 將其設定為 **Present** 以確保已安裝此套件。 **Ensure** 是 **WindowsPackageCab** 資源上的必要屬性。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

## <a name="example"></a>範例

以下範例設定會接受輸入參數，並確保安裝 `$Name` 參數所指定的 .cab 檔案。

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
