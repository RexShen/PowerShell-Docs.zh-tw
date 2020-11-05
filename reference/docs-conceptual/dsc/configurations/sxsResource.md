---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 匯入所安裝資源的特定版本
description: 此文章說明如何安裝特定版本的資源模組並將其匯入您的設定。
ms.openlocfilehash: bb7b3273a5a3fed94fecd90dd3ea1e623fbc332b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645046"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="4c509-104">匯入所安裝資源的特定版本</span><span class="sxs-lookup"><span data-stu-id="4c509-104">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="4c509-105">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4c509-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4c509-106">在 PowerShell 5.0 中，各個版本的 DSC 資源均可於一部電腦上並存安裝。</span><span class="sxs-lookup"><span data-stu-id="4c509-106">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="4c509-107">資源模組可將各個版本的資源儲存於以版本命名的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4c509-107">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="4c509-108">並存安裝各個資源版本</span><span class="sxs-lookup"><span data-stu-id="4c509-108">Installing separate resource versions side by side</span></span>

<span data-ttu-id="4c509-109">您可以使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 的 **MinimumVersion** 、 **MaximumVersion** 與 **RequiredVersion** 參數，指定要安裝的模組版本。</span><span class="sxs-lookup"><span data-stu-id="4c509-109">You can use the **MinimumVersion** , **MaximumVersion** , and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="4c509-110">呼叫 **Install-Module** 但未指定版本，會安裝最新的版本。</span><span class="sxs-lookup"><span data-stu-id="4c509-110">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="4c509-111">例如， **xFailOverCluster** 模組有多個版本，每個模組各包含一個 **xCluster** 資源。</span><span class="sxs-lookup"><span data-stu-id="4c509-111">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="4c509-112">呼叫 **Install-Module** 但未指定版本號碼，就會安裝最新版的模組。</span><span class="sxs-lookup"><span data-stu-id="4c509-112">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName           Version    Properties
-------------   ----          ----------           -------    ----------
PowerShell      xCluster      xFailOverCluster     1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="4c509-113">若要安裝特定版本的模組，請將 **RequiredVersion** 指定為 1.1.0.0。</span><span class="sxs-lookup"><span data-stu-id="4c509-113">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="4c509-114">這會並存安裝指定的版本與已安裝的版本。</span><span class="sxs-lookup"><span data-stu-id="4c509-114">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="4c509-115">現在，您會在使用 `Get-DSCResource` 時看到列出這兩個版本的模組。</span><span class="sxs-lookup"><span data-stu-id="4c509-115">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```Output
ImplementedAs   Name          ModuleName            Version    Properties
-------------   ----          ----------            -------    ----------
PowerShell      xCluster      xFailOverCluster      1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster      xFailOverCluster      1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="4c509-116">在設定中指定資源版本</span><span class="sxs-lookup"><span data-stu-id="4c509-116">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="4c509-117">如果電腦上安裝了各個資源版本，則當您在設定中使用該資源時，必須指定其版本。</span><span class="sxs-lookup"><span data-stu-id="4c509-117">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="4c509-118">若要這麼做，請指定 **Import-DscResource** 關鍵字的 **ModuleVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="4c509-118">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="4c509-119">若您無法指定安裝了多重版本之資源的資源模組版本，設定便會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4c509-119">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="4c509-120">下列設定示範如何指定要呼叫之資源的版本︰</span><span class="sxs-lookup"><span data-stu-id="4c509-120">The following configuration shows how to specify the version of the resource to call:</span></span>

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

<span data-ttu-id="4c509-121">PowerShell 4.0 中無法使用 Import-DscResource 的 ModuleVersion 參數。</span><span class="sxs-lookup"><span data-stu-id="4c509-121">The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="4c509-122">在 PowerShell 4.0 中您可以指定模組版本，方法是將模組規格物件傳遞至 Import-DscResource 的 ModuleName 參數。</span><span class="sxs-lookup"><span data-stu-id="4c509-122">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="4c509-123">模組規格物件是包含 ModuleName 與 RequiredVersion 機碼的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="4c509-123">A module specification object is a hash table that contains ModuleName and RequiredVersion keys.</span></span> <span data-ttu-id="4c509-124">例如：</span><span class="sxs-lookup"><span data-stu-id="4c509-124">For example:</span></span>

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

<span data-ttu-id="4c509-125">這也適用於 PowerShell 5.0 版，但仍然建議您使用 **ModuleVersion** 參數。</span><span class="sxs-lookup"><span data-stu-id="4c509-125">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c509-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c509-126">See also</span></span>

- [<span data-ttu-id="4c509-127">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="4c509-127">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="4c509-128">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4c509-128">DSC Resources</span></span>](../resources/resources.md)
