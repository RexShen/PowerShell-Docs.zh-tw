---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 巢狀設定
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75417861"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="78d47-103">巢狀 DSC 設定</span><span class="sxs-lookup"><span data-stu-id="78d47-103">Nesting DSC configurations</span></span>

<span data-ttu-id="78d47-104">巢狀設定 (也稱為複合設定) 係指在另一個設定內當成資源般來呼叫的設定。</span><span class="sxs-lookup"><span data-stu-id="78d47-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="78d47-105">這兩個設定必須定義在同一個檔案中。</span><span class="sxs-lookup"><span data-stu-id="78d47-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="78d47-106">讓我們看一個簡單範例：</span><span class="sxs-lookup"><span data-stu-id="78d47-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="78d47-107">在此範例中，`FileConfig` 採用兩個必要參數 **CopyFrom** 和 **CopyTo**，這兩個參數會用來作為 `File` 資源區塊中 **SourcePath** 和 **DestinationPath** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="78d47-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="78d47-108">`NestedConfig` 設定會將 `FileConfig` 當成資源般來呼叫。</span><span class="sxs-lookup"><span data-stu-id="78d47-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="78d47-109">`NestedConfig` 資源區塊中的屬性 (**CopyFrom** 和 **CopyTo**) 是 `FileConfig` 設定的參數。</span><span class="sxs-lookup"><span data-stu-id="78d47-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="78d47-110">DSC 目前不支援將設定內嵌在巢狀設定內。</span><span class="sxs-lookup"><span data-stu-id="78d47-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="78d47-111">您只能將設定內嵌一層的深度。</span><span class="sxs-lookup"><span data-stu-id="78d47-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="78d47-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78d47-112">See Also</span></span>

- [<span data-ttu-id="78d47-113">複合資源 -- 把 DSC 設定當做資源使用</span><span class="sxs-lookup"><span data-stu-id="78d47-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)