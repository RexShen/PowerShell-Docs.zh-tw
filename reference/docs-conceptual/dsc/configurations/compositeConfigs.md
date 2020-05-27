---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 巢狀設定
ms.openlocfilehash: e74c0fe1d7f7b198c2d6f796c0bf120eb0ec21d9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564027"
---
# <a name="nesting-dsc-configurations"></a>巢狀 DSC 設定

巢狀設定 (也稱為複合設定) 係指在另一個設定內當成資源般來呼叫的設定。 這兩個設定必須定義在同一個檔案中。

讓我們看一個簡單範例：

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
    {
        SourcePath = $CopyFrom
        DestinationPath = $CopyTo
        Ensure = 'Present'
    }
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

在此範例中，`FileConfig` 採用兩個必要參數 **CopyFrom** 和 **CopyTo**，這兩個參數會用來作為 **資源區塊中**SourcePath**和**DestinationPath`File` 屬性的值。 `NestedConfig` 設定會將 `FileConfig` 當成資源般來呼叫。 `NestedConfig` 資源區塊中的屬性 (**CopyFrom** 和 **CopyTo**) 是 `FileConfig` 設定的參數。

DSC 目前不支援將設定內嵌在巢狀設定內。 您只能將設定內嵌一層的深度。

## <a name="see-also"></a>另請參閱

- [複合資源 -- 把 DSC 設定當做資源使用](../resources/authoringResourceComposite.md)
