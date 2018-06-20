---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187525"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="b4a55-102">允許在設定中的相同重複資源</span><span class="sxs-lookup"><span data-stu-id="b4a55-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="b4a55-103">DSC 不允許或不處理設定中定義的衝突資源。</span><span class="sxs-lookup"><span data-stu-id="b4a55-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="b4a55-104">它並不會去嘗試解決衝突，而是只會失敗。</span><span class="sxs-lookup"><span data-stu-id="b4a55-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="b4a55-105">當設定重複使用透過複合資源而變得更有用時，衝突發生頻率將會提高。</span><span class="sxs-lookup"><span data-stu-id="b4a55-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="b4a55-106">當衝突資源的定義相同時，DSC 應該進行智慧判斷並允許此情況。</span><span class="sxs-lookup"><span data-stu-id="b4a55-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="b4a55-107">在此版本中，我們支援具有相同定義的多個資源執行個體︰</span><span class="sxs-lookup"><span data-stu-id="b4a55-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="b4a55-108">在舊版中，因為 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 執行個體在盡力確保 「網頁伺服器」 角色已安裝時發生衝突，因此會出現編譯失敗的結果。</span><span class="sxs-lookup"><span data-stu-id="b4a55-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="b4a55-109">請注意在這兩種設定中，*所有*正在設定的屬性都是相同的。</span><span class="sxs-lookup"><span data-stu-id="b4a55-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="b4a55-110">由於這兩個資源中的*所有*屬性相同，現在這會讓編譯成功完成。</span><span class="sxs-lookup"><span data-stu-id="b4a55-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="b4a55-111">如果任何屬性在兩個資源之間的有所差異，它們將不會被視為相同，而且編譯會失敗︰</span><span class="sxs-lookup"><span data-stu-id="b4a55-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="b4a55-112">此非常類似的設定將會失敗，因為 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 資源不再相同，因此發生衝突。</span><span class="sxs-lookup"><span data-stu-id="b4a55-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
