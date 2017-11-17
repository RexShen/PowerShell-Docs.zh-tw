---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WaitForAll 資源"
ms.openlocfilehash: dcc23ad4e6905bc277ad39348350d5425fc90ad7
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="0207d-103">DSC WaitForAll 資源</span><span class="sxs-lookup"><span data-stu-id="0207d-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="0207d-104">適用於︰Windows PowerShell 5.0 及更新版本</span><span class="sxs-lookup"><span data-stu-id="0207d-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="0207d-105">您可以在 [DSC 設定](configurations.md)中的節點區塊內使用 **WaitForAll**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="0207d-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="0207d-106">如果 **ResourceName** 屬性所指定的資源在 **NodeName** 屬性所定義的所有目標節點上都處於預期狀態，此資源即可視為成功。</span><span class="sxs-lookup"><span data-stu-id="0207d-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="0207d-107">語法</span><span class="sxs-lookup"><span data-stu-id="0207d-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="0207d-108">[內容]</span><span class="sxs-lookup"><span data-stu-id="0207d-108">Properties</span></span>

|  <span data-ttu-id="0207d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0207d-109">Property</span></span>  |  <span data-ttu-id="0207d-110">描述</span><span class="sxs-lookup"><span data-stu-id="0207d-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0207d-111">ResourceName</span><span class="sxs-lookup"><span data-stu-id="0207d-111">ResourceName</span></span>| <span data-ttu-id="0207d-112">所要依據的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="0207d-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="0207d-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="0207d-113">NodeName</span></span>| <span data-ttu-id="0207d-114">所要依據之資源的目標節點。</span><span class="sxs-lookup"><span data-stu-id="0207d-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="0207d-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="0207d-115">RetryIntervalSec</span></span>| <span data-ttu-id="0207d-116">進行重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="0207d-116">The number of seconds before retrying.</span></span> <span data-ttu-id="0207d-117">最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="0207d-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="0207d-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="0207d-118">RetryCount</span></span>| <span data-ttu-id="0207d-119">重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="0207d-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="0207d-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0207d-120">ThrottleLimit</span></span>| <span data-ttu-id="0207d-121">可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="0207d-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="0207d-122">預設值為 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="0207d-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="0207d-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0207d-123">DependsOn</span></span> | <span data-ttu-id="0207d-124">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="0207d-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0207d-125">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0207d-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="0207d-126">範例</span><span class="sxs-lookup"><span data-stu-id="0207d-126">Example</span></span>

<span data-ttu-id="0207d-127">如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="0207d-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

