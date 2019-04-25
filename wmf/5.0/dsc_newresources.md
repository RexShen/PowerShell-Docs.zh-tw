---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 64a00e041bbeeea117db43116b486e83dfe923b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085825"
---
# <a name="new-built-in-dsc-resources"></a><span data-ttu-id="95b12-102">新的內建 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="95b12-102">New built-in DSC resources</span></span>

<span data-ttu-id="95b12-103">WMF 5.0 RTM 有 4 個新的 DSC 資源︰</span><span class="sxs-lookup"><span data-stu-id="95b12-103">WMF 5.0 RTM has 4 new DSC resources:</span></span>
* <span data-ttu-id="95b12-104">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="95b12-104">WindowsFeatureSet</span></span>
* <span data-ttu-id="95b12-105">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="95b12-105">WindowsOptionalFeatureSet</span></span>
* <span data-ttu-id="95b12-106">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="95b12-106">ServiceSet</span></span>
* <span data-ttu-id="95b12-107">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="95b12-107">ProcessSet</span></span>

<span data-ttu-id="95b12-108">這些資源提供了簡單的方法來設定使用單一資源呼叫的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="95b12-108">These resources provide an easy way to configure multiple instances using a single resource call.</span></span>

## <a name="windowsfeatureset"></a><span data-ttu-id="95b12-109">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="95b12-109">WindowsFeatureSet</span></span>

```powershell
# Get the syntax of WindowsFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsFeatureSet -Syntax

WindowsFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [Ensure = [String]]
    [Source = [String]]
    [IncludeAllSubFeature = [Boolean]]
    [Credential = [PSCredential]]
    [LogPath = [String]]
}
```

## <a name="windowsoptionalfeatureset"></a><span data-ttu-id="95b12-110">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="95b12-110">WindowsOptionalFeatureSet</span></span>

```powershell
# Get the syntax of WindowsOptionalFeatureSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name WindowsOptionalFeatureSet -Syntax

WindowsOptionalFeatureSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    Ensure = [String]
    [Source = [String[]]]
    [RemoveFilesOnDisable = [Boolean]]
    [LogPath = [String]]
    [NoWindowsUpdateCheck = [Boolean]]
    [LogLevel = [String]]
}
```

## <a name="serviceset"></a><span data-ttu-id="95b12-111">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="95b12-111">ServiceSet</span></span>

```powershell
# Get the syntax of ServiceSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ServiceSet -Syntax

ServiceSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Name = [String[]]
    [StartupType = [String]]
    [BuiltInAccount = [String]]
    [State = [String]]
    [Ensure = [String]]
    [Credential = [PSCredential]]
}
```

## <a name="processset"></a><span data-ttu-id="95b12-112">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="95b12-112">ProcessSet</span></span>

```powershell
# Get the syntax of ProcessSet resource
Get-DscResource -Module psdesiredstateconfiguration -Name ProcessSet -Syntax

ProcessSet [String] #ResourceName
{
    [DependsOn = [String[]]]
    Path = [String[]]
    [Credential = [PSCredential]]
    [Ensure = [String]]
    [StandardOutputPath = [String]]
    [StandardErrorPath = [String]]
    [StandardInputPath = [String]]
    [WorkingDirectory = [String]]
}
```
