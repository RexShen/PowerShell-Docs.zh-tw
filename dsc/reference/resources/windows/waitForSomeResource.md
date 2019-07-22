---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC WaitForSome 資源
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726779"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="ab5ff-103">DSC WaitForSome 資源</span><span class="sxs-lookup"><span data-stu-id="ab5ff-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="ab5ff-104">適用於：Windows PowerShell 5.0 及更新版本</span><span class="sxs-lookup"><span data-stu-id="ab5ff-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="ab5ff-105">您可以在 [DSC 設定](../../../configurations/configurations.md)中的節點區塊內使用 **WaitForSome**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ab5ff-106">如果 **ResourceName** 屬性所指定的資源處於預期狀態的節點達到 **NodeName** 屬性所定義的節點數目下限 (由 **NodeCount** 指定)，此資源即可視為成功。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="ab5ff-107">**WaitForSome** 資源使用 Windows 遠端管理來檢查其他節點的狀態。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="ab5ff-108">如需 WinRM 連接埠和安全性需求的詳細資訊，請參閱 [PowerShell 遠端安全性考量](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="ab5ff-109">語法</span><span class="sxs-lookup"><span data-stu-id="ab5ff-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ab5ff-110">Properties</span><span class="sxs-lookup"><span data-stu-id="ab5ff-110">Properties</span></span>

|  <span data-ttu-id="ab5ff-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ab5ff-111">Property</span></span>  |  <span data-ttu-id="ab5ff-112">描述</span><span class="sxs-lookup"><span data-stu-id="ab5ff-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="ab5ff-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="ab5ff-113">NodeCount</span></span>| <span data-ttu-id="ab5ff-114">若要將此資源視為成功，必須處於預期狀態的節點數目下限。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="ab5ff-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="ab5ff-115">NodeName</span></span>| <span data-ttu-id="ab5ff-116">所要依據之資源的目標節點。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="ab5ff-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="ab5ff-117">ResourceName</span></span>| <span data-ttu-id="ab5ff-118">所要依據的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-118">The resource name to depend on.</span></span> <span data-ttu-id="ab5ff-119">若此資源屬於其他設定，請將名稱的格式設定為 "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span><span class="sxs-lookup"><span data-stu-id="ab5ff-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="ab5ff-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ab5ff-120">RetryIntervalSec</span></span>| <span data-ttu-id="ab5ff-121">進行重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-121">The number of seconds before retrying.</span></span> <span data-ttu-id="ab5ff-122">最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-122">Minimum is 1.</span></span>|
| <span data-ttu-id="ab5ff-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ab5ff-123">RetryCount</span></span>| <span data-ttu-id="ab5ff-124">重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="ab5ff-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ab5ff-125">ThrottleLimit</span></span>| <span data-ttu-id="ab5ff-126">可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ab5ff-127">預設值為 new-cimsession default。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="ab5ff-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ab5ff-128">DependsOn</span></span> | <span data-ttu-id="ab5ff-129">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ab5ff-130">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="ab5ff-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="ab5ff-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ab5ff-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="ab5ff-132">請參閱[以使用者認證執行 DSC](https://docs.microsoft.com/powershell/dsc/runasuser)</span><span class="sxs-lookup"><span data-stu-id="ab5ff-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="ab5ff-133">範例</span><span class="sxs-lookup"><span data-stu-id="ab5ff-133">Example</span></span>

<span data-ttu-id="ab5ff-134">如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="ab5ff-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
