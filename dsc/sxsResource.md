---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "使用多個版本的資源"
ms.openlocfilehash: 5ca4eadfe23a4675e1b81b86d4274d7f113228fe
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="9bc4c-103">使用多個版本的資源</span><span class="sxs-lookup"><span data-stu-id="9bc4c-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="9bc4c-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9bc4c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9bc4c-105">在 PowerShell 5.0，DSC 資源可以有多個版本，且各版本可於一部電腦上並存安裝。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="9bc4c-106">而其運作方式則是在相同的模組資料夾中，包含多個版本的資源模組。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="9bc4c-107">並存安裝多個資源版本</span><span class="sxs-lookup"><span data-stu-id="9bc4c-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="9bc4c-108">您可以使用 [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) Cmdlet 的 **MinimumVersion**、**MaximumVersion** 與 **RequiredVersion** 參數，指定要安裝的模組版本。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="9bc4c-109">呼叫 **Install-Module** 但未指定版本，會安裝最新的版本。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="9bc4c-110">例如，多個版本的 **xFailOverCluster** 模組，每個皆包含 **xCluster** 資源。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="9bc4c-111">呼叫 **Install-Module** 但未指定版本號碼的結果如下：</span><span class="sxs-lookup"><span data-stu-id="9bc4c-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="9bc4c-112">現在，如果再次呼叫 **Install-Module**，但指定 **RequiredVersion** 為 1.1.0.0，會產生以下結果︰</span><span class="sxs-lookup"><span data-stu-id="9bc4c-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="9bc4c-113">在設定中指定資源版本</span><span class="sxs-lookup"><span data-stu-id="9bc4c-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="9bc4c-114">如果在電腦上安裝了多個資源，當您在設定中使用該資源時，必須指定版本。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="9bc4c-115">若要這麼做，請指定 **Import-DscResource** 關鍵字的 **ModuleVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="9bc4c-116">若您無法指定安裝了多重版本之資源的資源模組版本，設定便會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="9bc4c-117">下列設定示範如何指定要呼叫之資源的版本︰</span><span class="sxs-lookup"><span data-stu-id="9bc4c-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="9bc4c-118">注意︰PowerShell 4.0 中無法使用 Import-DscResource 的 ModuleVersion 參數。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="9bc4c-119">在 PowerShell 4.0 中您可以指定模組版本，方法是將模組規格物件傳遞至 Import-DscResource 的 ModuleName 參數。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="9bc4c-120">模組規格物件是包含 ModuleName 與 RequiredVersion 索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="9bc4c-121">例如：</span><span class="sxs-lookup"><span data-stu-id="9bc4c-121">For example:</span></span>

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

<span data-ttu-id="9bc4c-122">這也適用於 PowerShell 5.0 版，但仍然建議您使用 **ModuleVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="9bc4c-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bc4c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bc4c-123">See also</span></span>
* [<span data-ttu-id="9bc4c-124">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="9bc4c-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="9bc4c-125">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="9bc4c-125">DSC Resources</span></span>](resources.md)

