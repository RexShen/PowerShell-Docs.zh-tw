---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WaitForSome 資源"
ms.openlocfilehash: 8b0ad0dbd31816cc673c7f77945927987e90e08b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="0362b-103">DSC WaitForSome 資源</span><span class="sxs-lookup"><span data-stu-id="0362b-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="0362b-104">適用於︰Windows PowerShell 5.0 及更新版本</span><span class="sxs-lookup"><span data-stu-id="0362b-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="0362b-105">您可以在 [DSC 設定](configurations.md)中的節點區塊內使用 **WaitForAny**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="0362b-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="0362b-106">如果 **ResourceName** 屬性所指定的資源處於預期狀態的節點達到 **NodeName** 屬性所定義的節點數目下限 (由 **NodeCount** 指定)，此資源即可視為成功。</span><span class="sxs-lookup"><span data-stu-id="0362b-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 


## <a name="syntax"></a><span data-ttu-id="0362b-107">語法</span><span class="sxs-lookup"><span data-stu-id="0362b-107">Syntax</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

## <a name="properties"></a><span data-ttu-id="0362b-108">Properties</span><span class="sxs-lookup"><span data-stu-id="0362b-108">Properties</span></span>

|  <span data-ttu-id="0362b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0362b-109">Property</span></span>  |  <span data-ttu-id="0362b-110">描述</span><span class="sxs-lookup"><span data-stu-id="0362b-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0362b-111">NodeCount</span><span class="sxs-lookup"><span data-stu-id="0362b-111">NodeCount</span></span>| <span data-ttu-id="0362b-112">若要將此資源視為成功，必須處於預期狀態的節點數目下限。</span><span class="sxs-lookup"><span data-stu-id="0362b-112">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="0362b-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="0362b-113">NodeName</span></span>| <span data-ttu-id="0362b-114">所要依據之資源的目標節點。</span><span class="sxs-lookup"><span data-stu-id="0362b-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="0362b-115">ResourceName</span><span class="sxs-lookup"><span data-stu-id="0362b-115">ResourceName</span></span>| <span data-ttu-id="0362b-116">所要依據的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="0362b-116">The resource name to depend on.</span></span> <span data-ttu-id="0362b-117">若此資源屬於其他設定，請將名稱的格式設定為 "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span><span class="sxs-lookup"><span data-stu-id="0362b-117">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>| 
| <span data-ttu-id="0362b-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="0362b-118">RetryIntervalSec</span></span>| <span data-ttu-id="0362b-119">進行重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="0362b-119">The number of seconds before retrying.</span></span> <span data-ttu-id="0362b-120">最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="0362b-120">Minimum is 1.</span></span>| 
| <span data-ttu-id="0362b-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="0362b-121">RetryCount</span></span>| <span data-ttu-id="0362b-122">重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="0362b-122">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="0362b-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="0362b-123">ThrottleLimit</span></span>| <span data-ttu-id="0362b-124">可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="0362b-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="0362b-125">預設值為 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="0362b-125">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="0362b-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0362b-126">DependsOn</span></span> | <span data-ttu-id="0362b-127">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="0362b-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0362b-128">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0362b-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="0362b-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0362b-129">PsDscRunAsCredential</span></span> | <span data-ttu-id="0362b-130">請參閱[以使用者認證執行 DSC](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="0362b-130">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |


## <a name="example"></a><span data-ttu-id="0362b-131">範例</span><span class="sxs-lookup"><span data-stu-id="0362b-131">Example</span></span>

<span data-ttu-id="0362b-132">如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="0362b-132">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

