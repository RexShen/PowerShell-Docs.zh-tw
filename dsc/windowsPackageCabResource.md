---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WindowsPackageCab 資源"
ms.openlocfilehash: 1d7c8d9bf45d2eda8734daa8877315d219662c75
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab 資源

> 適用於︰Windows PowerShell 5.1 及更新版本

Windows PowerShell 預期狀態設定 (DSC) 中的 **WindowsPackageCab** 資源提供一個機制，可在目標節點上安裝或解除安裝 Windows 封包 (.cab) 套件。

目標節點上必須安裝 DISM PowerShell 模組。 如需相關資訊，請參閱[在 Windows PowerShell 中使用 DISM](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14)。 


## <a name="syntax"></a>語法

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Properties

|  屬性  |  描述   | 
|---|---| 
| 名稱| 指出您想要確保其特定狀態的套件名稱。| 
| Ensure| 指出是否要安裝此套件。 設定此屬性為 "Absent" 以確保不會安裝此套件 (或如果已安裝，則解除安裝此套件)。 將它設定為 "Present" (預設值) 以確保已安裝此套件。|
| 路徑| 指出套件所在的檔案路徑| 
| LogPath| 指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

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

