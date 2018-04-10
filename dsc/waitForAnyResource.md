---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: DSC WaitForAny 資源
ms.openlocfilehash: 3d73c16397d9a18805184e6a5bb8561483144898
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="debb0-103">DSC WaitForAny 資源</span><span class="sxs-lookup"><span data-stu-id="debb0-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="debb0-104">適用於︰Windows PowerShell 5.1 及更新版本</span><span class="sxs-lookup"><span data-stu-id="debb0-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="debb0-105">您可以在 [DSC 設定](configurations.md)中的節點區塊內使用 **WaitForSome**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="debb0-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="debb0-106">如果 **ResourceName** 屬性所指定的資源在 **NodeName** 屬性所定義的任何目標節點上處於預期狀態，此資源即可視為成功。</span><span class="sxs-lookup"><span data-stu-id="debb0-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="debb0-107">語法</span><span class="sxs-lookup"><span data-stu-id="debb0-107">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="debb0-108">Properties</span><span class="sxs-lookup"><span data-stu-id="debb0-108">Properties</span></span>

|  <span data-ttu-id="debb0-109">屬性</span><span class="sxs-lookup"><span data-stu-id="debb0-109">Property</span></span>  |  <span data-ttu-id="debb0-110">描述</span><span class="sxs-lookup"><span data-stu-id="debb0-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="debb0-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="debb0-111">ResourceName</span></span>| <span data-ttu-id="debb0-112">所要依據的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="debb0-112">The resource name to depend on.</span></span> <span data-ttu-id="debb0-113">若此資源屬於其他設定，請將名稱的格式設定為 "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span><span class="sxs-lookup"><span data-stu-id="debb0-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="debb0-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="debb0-114">NodeName</span></span>| <span data-ttu-id="debb0-115">所要依據之資源的目標節點。</span><span class="sxs-lookup"><span data-stu-id="debb0-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="debb0-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="debb0-116">RetryIntervalSec</span></span>| <span data-ttu-id="debb0-117">進行重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="debb0-117">The number of seconds before retrying.</span></span> <span data-ttu-id="debb0-118">最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="debb0-118">Minimum is 1.</span></span>|
| <span data-ttu-id="debb0-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="debb0-119">RetryCount</span></span>| <span data-ttu-id="debb0-120">重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="debb0-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="debb0-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="debb0-121">ThrottleLimit</span></span>| <span data-ttu-id="debb0-122">可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="debb0-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="debb0-123">預設值為 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="debb0-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="debb0-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="debb0-124">DependsOn</span></span> | <span data-ttu-id="debb0-125">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="debb0-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="debb0-126">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="debb0-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="debb0-127">範例</span><span class="sxs-lookup"><span data-stu-id="debb0-127">Example</span></span>

<span data-ttu-id="debb0-128">如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="debb0-128">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>