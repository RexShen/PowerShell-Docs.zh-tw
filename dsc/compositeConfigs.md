---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "巢狀設定"
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a>巢狀 DSC 設定

巢狀設定 (也稱為複合設定) 是在另一個設定中將它當成資源般呼叫的設定。
這兩個設定必須定義在同一個檔案中。

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

在此範例中，`FileConfig` 採用兩個必要參數 **CopyFrom** 和 **CopyTo**，這兩個參數是用來做為 `File` 資源區塊中**SourcePath** 和 **DestinationPath** 屬性的值。 `NestedConfig` 設定會將 `FileConfig` 當成資源般來呼叫。
`NestedConfig` 資源區塊中的屬性 (**CopyFrom** 和 **CopyTo**) 是 `FileConfig` 設定的參數。

## <a name="see-also"></a>另請參閱

- [複合資源 -- 把 DSC 設定當做資源使用](authoringResourceComposite.md)

