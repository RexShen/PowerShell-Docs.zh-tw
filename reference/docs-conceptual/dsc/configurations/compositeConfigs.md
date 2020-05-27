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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="b1258-103">巢狀 DSC 設定</span><span class="sxs-lookup"><span data-stu-id="b1258-103">Nesting DSC configurations</span></span>

<span data-ttu-id="b1258-104">巢狀設定 (也稱為複合設定) 係指在另一個設定內當成資源般來呼叫的設定。</span><span class="sxs-lookup"><span data-stu-id="b1258-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="b1258-105">這兩個設定必須定義在同一個檔案中。</span><span class="sxs-lookup"><span data-stu-id="b1258-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="b1258-106">讓我們看一個簡單範例：</span><span class="sxs-lookup"><span data-stu-id="b1258-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="b1258-107">在此範例中，`FileConfig` 採用兩個必要參數 **CopyFrom** 和 **CopyTo**，這兩個參數會用來作為 **資源區塊中**SourcePath**和**DestinationPath`File` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b1258-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="b1258-108">`NestedConfig` 設定會將 `FileConfig` 當成資源般來呼叫。</span><span class="sxs-lookup"><span data-stu-id="b1258-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="b1258-109">`NestedConfig` 資源區塊中的屬性 (**CopyFrom** 和 **CopyTo**) 是 `FileConfig` 設定的參數。</span><span class="sxs-lookup"><span data-stu-id="b1258-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="b1258-110">DSC 目前不支援將設定內嵌在巢狀設定內。</span><span class="sxs-lookup"><span data-stu-id="b1258-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="b1258-111">您只能將設定內嵌一層的深度。</span><span class="sxs-lookup"><span data-stu-id="b1258-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1258-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1258-112">See Also</span></span>

- [<span data-ttu-id="b1258-113">複合資源 -- 把 DSC 設定當做資源使用</span><span class="sxs-lookup"><span data-stu-id="b1258-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
