---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 匯入所安裝資源的特定版本
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400628"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="86d8e-103">匯入所安裝資源的特定版本</span><span class="sxs-lookup"><span data-stu-id="86d8e-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="86d8e-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="86d8e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="86d8e-105">在 PowerShell 5.0 中，可以並存的電腦上安裝的 DSC 資源的不同版本。</span><span class="sxs-lookup"><span data-stu-id="86d8e-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="86d8e-106">資源模組都可以儲存在名為資料夾的版本的不同版本的資源。</span><span class="sxs-lookup"><span data-stu-id="86d8e-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="86d8e-107">安裝個別的資源版本並排顯示</span><span class="sxs-lookup"><span data-stu-id="86d8e-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="86d8e-108">您可以使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 的 **MinimumVersion**、**MaximumVersion** 與 **RequiredVersion** 參數，指定要安裝的模組版本。</span><span class="sxs-lookup"><span data-stu-id="86d8e-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="86d8e-109">呼叫 **Install-Module** 但未指定版本，會安裝最新的版本。</span><span class="sxs-lookup"><span data-stu-id="86d8e-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="86d8e-110">例如，**xFailOverCluster** 模組有多個版本，每個模組各包含一個 **xCluster** 資源。</span><span class="sxs-lookup"><span data-stu-id="86d8e-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="86d8e-111">呼叫**Install-module**但未指定版本號碼會安裝最新版的模組。</span><span class="sxs-lookup"><span data-stu-id="86d8e-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="86d8e-112">若要安裝特定版本的模組，指定**RequiredVersion**為 1.1.0.0。</span><span class="sxs-lookup"><span data-stu-id="86d8e-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="86d8e-113">這會安裝指定的版本並存安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="86d8e-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="86d8e-114">現在，您會看到兩者的模組版本列出當您使用`Get-DSCResource`。</span><span class="sxs-lookup"><span data-stu-id="86d8e-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="86d8e-115">在設定中指定資源版本</span><span class="sxs-lookup"><span data-stu-id="86d8e-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="86d8e-116">如果您有不同的資源版本的電腦上安裝時，您必須指定該資源的版本，當您在組態中使用它。</span><span class="sxs-lookup"><span data-stu-id="86d8e-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="86d8e-117">若要這麼做，請指定 **Import-DscResource** 關鍵字的 **ModuleVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="86d8e-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="86d8e-118">若您無法指定安裝了多重版本之資源的資源模組版本，設定便會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="86d8e-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="86d8e-119">下列設定示範如何指定要呼叫之資源的版本︰</span><span class="sxs-lookup"><span data-stu-id="86d8e-119">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="86d8e-120">注意：無法在 PowerShell 4.0 中使用 Import-dscresource 的 ModuleVersion 參數。</span><span class="sxs-lookup"><span data-stu-id="86d8e-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="86d8e-121">在 PowerShell 4.0 中您可以指定模組版本，方法是將模組規格物件傳遞至 Import-DscResource 的 ModuleName 參數。</span><span class="sxs-lookup"><span data-stu-id="86d8e-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="86d8e-122">模組規格物件是包含 ModuleName 與 RequiredVersion 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="86d8e-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="86d8e-123">例如：</span><span class="sxs-lookup"><span data-stu-id="86d8e-123">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="86d8e-124">這也適用於 PowerShell 5.0 版，但仍然建議您使用 **ModuleVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="86d8e-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="86d8e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86d8e-125">See also</span></span>

- [<span data-ttu-id="86d8e-126">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="86d8e-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="86d8e-127">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="86d8e-127">DSC Resources</span></span>](../resources/resources.md)
