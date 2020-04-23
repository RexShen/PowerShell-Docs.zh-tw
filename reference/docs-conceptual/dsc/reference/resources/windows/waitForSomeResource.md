---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WaitForSome 資源
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952975"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="63fe1-103">DSC WaitForSome 資源</span><span class="sxs-lookup"><span data-stu-id="63fe1-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="63fe1-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="63fe1-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="63fe1-105">您可以在 [DSC 設定](../../../configurations/configurations.md)中的節點區塊內使用 **WaitForSome**「預期狀態設定」(DSC) 資源，以指定與其他節點上之設定的相依性。</span><span class="sxs-lookup"><span data-stu-id="63fe1-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="63fe1-106">如果 **ResourceName** 屬性所指定的資源處於預期狀態的節點達到 **NodeName** 屬性所定義的節點數目下限 (由 **NodeCount** 指定)，此資源即可視為成功。</span><span class="sxs-lookup"><span data-stu-id="63fe1-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="63fe1-107">**WaitForSome** 資源使用 Windows 遠端管理來檢查其他節點的狀態。</span><span class="sxs-lookup"><span data-stu-id="63fe1-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="63fe1-108">如需 WinRM 連接埠和安全性需求的詳細資訊，請參閱 [PowerShell 遠端安全性考量](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="63fe1-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="63fe1-109">語法</span><span class="sxs-lookup"><span data-stu-id="63fe1-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="63fe1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="63fe1-110">Properties</span></span>

|<span data-ttu-id="63fe1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="63fe1-111">Property</span></span> |<span data-ttu-id="63fe1-112">描述</span><span class="sxs-lookup"><span data-stu-id="63fe1-112">Description</span></span> |
|---|---|
|<span data-ttu-id="63fe1-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="63fe1-113">NodeCount</span></span> |<span data-ttu-id="63fe1-114">若要將此資源視為成功，必須處於預期狀態的節點數目下限。</span><span class="sxs-lookup"><span data-stu-id="63fe1-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="63fe1-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="63fe1-115">NodeName</span></span> |<span data-ttu-id="63fe1-116">所要依據之資源的目標節點。</span><span class="sxs-lookup"><span data-stu-id="63fe1-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="63fe1-117">ResourceName</span><span class="sxs-lookup"><span data-stu-id="63fe1-117">ResourceName</span></span> |<span data-ttu-id="63fe1-118">所要依據的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="63fe1-118">The resource name to depend on.</span></span> <span data-ttu-id="63fe1-119">如果此資源屬於不同的設定，請將名稱格式化為 `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`。</span><span class="sxs-lookup"><span data-stu-id="63fe1-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="63fe1-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="63fe1-120">RetryIntervalSec</span></span> |<span data-ttu-id="63fe1-121">進行重試之前的秒數。</span><span class="sxs-lookup"><span data-stu-id="63fe1-121">The number of seconds before retrying.</span></span> <span data-ttu-id="63fe1-122">最小值為 1。</span><span class="sxs-lookup"><span data-stu-id="63fe1-122">Minimum is 1.</span></span> |
|<span data-ttu-id="63fe1-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="63fe1-123">RetryCount</span></span> |<span data-ttu-id="63fe1-124">重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="63fe1-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="63fe1-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="63fe1-125">ThrottleLimit</span></span> |<span data-ttu-id="63fe1-126">可同時連線的電腦數目。</span><span class="sxs-lookup"><span data-stu-id="63fe1-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="63fe1-127">預設值為 `New-CimSession` 預設值。</span><span class="sxs-lookup"><span data-stu-id="63fe1-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="63fe1-128">通用屬性</span><span class="sxs-lookup"><span data-stu-id="63fe1-128">Common properties</span></span>

|<span data-ttu-id="63fe1-129">屬性</span><span class="sxs-lookup"><span data-stu-id="63fe1-129">Property</span></span> |<span data-ttu-id="63fe1-130">描述</span><span class="sxs-lookup"><span data-stu-id="63fe1-130">Description</span></span> |
|---|---|
|<span data-ttu-id="63fe1-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="63fe1-131">DependsOn</span></span> |<span data-ttu-id="63fe1-132">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="63fe1-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="63fe1-133">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="63fe1-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="63fe1-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="63fe1-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="63fe1-135">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="63fe1-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="63fe1-136">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="63fe1-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="63fe1-137">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="63fe1-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="63fe1-138">範例</span><span class="sxs-lookup"><span data-stu-id="63fe1-138">Example</span></span>

<span data-ttu-id="63fe1-139">如需有關如何使用此資源的範例，請參閱[指定跨節點相依性](../../../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="63fe1-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>