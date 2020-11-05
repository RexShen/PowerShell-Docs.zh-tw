---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 巢狀設定
description: DSC 允許您透過將設定巢狀處理於另一個設定中來建立複合設定。
ms.openlocfilehash: d7a81cb9673126e92e9185aacf19c5c7c17da8ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667414"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="8e263-104">巢狀 DSC 設定</span><span class="sxs-lookup"><span data-stu-id="8e263-104">Nesting DSC configurations</span></span>

<span data-ttu-id="8e263-105">巢狀設定 (也稱為複合設定) 係指在另一個設定內當成資源般來呼叫的設定。</span><span class="sxs-lookup"><span data-stu-id="8e263-105">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="8e263-106">這兩個設定必須定義在同一個檔案中。</span><span class="sxs-lookup"><span data-stu-id="8e263-106">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="8e263-107">讓我們看一個簡單範例：</span><span class="sxs-lookup"><span data-stu-id="8e263-107">Let's look at a simple example:</span></span>

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

<span data-ttu-id="8e263-108">在此範例中，`FileConfig` 採用兩個必要參數 **CopyFrom** 和 **CopyTo** ，這兩個參數會用來作為 `File` 資源區塊中 **SourcePath** 和 **DestinationPath** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8e263-108">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo** , which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="8e263-109">`NestedConfig` 設定會將 `FileConfig` 當成資源般來呼叫。</span><span class="sxs-lookup"><span data-stu-id="8e263-109">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="8e263-110">`NestedConfig` 資源區塊中的屬性 ( **CopyFrom** 和 **CopyTo** ) 是 `FileConfig` 設定的參數。</span><span class="sxs-lookup"><span data-stu-id="8e263-110">The properties in the `NestedConfig` resource block ( **CopyFrom** and **CopyTo** ) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="8e263-111">DSC 目前不支援將設定內嵌在巢狀設定內。</span><span class="sxs-lookup"><span data-stu-id="8e263-111">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="8e263-112">您只能將設定內嵌一層的深度。</span><span class="sxs-lookup"><span data-stu-id="8e263-112">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e263-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e263-113">See Also</span></span>

- [<span data-ttu-id="8e263-114">複合資源 -- 把 DSC 設定當做資源使用</span><span class="sxs-lookup"><span data-stu-id="8e263-114">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
