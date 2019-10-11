---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxService 資源
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954835"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="99c0b-103">DSC for Linux nxService 資源</span><span class="sxs-lookup"><span data-stu-id="99c0b-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="99c0b-104">PowerShell 預期狀態設定 (DSC) 的 **nxService** 資源會提供一個機制，在 Linux 節點管理服務。</span><span class="sxs-lookup"><span data-stu-id="99c0b-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="99c0b-105">語法</span><span class="sxs-lookup"><span data-stu-id="99c0b-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="99c0b-106">Properties</span><span class="sxs-lookup"><span data-stu-id="99c0b-106">Properties</span></span>

|<span data-ttu-id="99c0b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="99c0b-107">Property</span></span> |<span data-ttu-id="99c0b-108">描述</span><span class="sxs-lookup"><span data-stu-id="99c0b-108">Description</span></span> |
|---|---|
|<span data-ttu-id="99c0b-109">名稱</span><span class="sxs-lookup"><span data-stu-id="99c0b-109">Name</span></span> |<span data-ttu-id="99c0b-110">要設定的服務/精靈名稱。</span><span class="sxs-lookup"><span data-stu-id="99c0b-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="99c0b-111">控制器</span><span class="sxs-lookup"><span data-stu-id="99c0b-111">Controller</span></span> |<span data-ttu-id="99c0b-112">設定服務時所要使用的服務控制站類型。</span><span class="sxs-lookup"><span data-stu-id="99c0b-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="99c0b-113">啟用</span><span class="sxs-lookup"><span data-stu-id="99c0b-113">Enabled</span></span> |<span data-ttu-id="99c0b-114">指出是否在開機時啟動服務。</span><span class="sxs-lookup"><span data-stu-id="99c0b-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="99c0b-115">State</span><span class="sxs-lookup"><span data-stu-id="99c0b-115">State</span></span> |<span data-ttu-id="99c0b-116">表示服務是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="99c0b-116">Indicates whether the service is running.</span></span> <span data-ttu-id="99c0b-117">將此屬性設定為 **Stopped**，以確保服務未正在執行中。</span><span class="sxs-lookup"><span data-stu-id="99c0b-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="99c0b-118">將其設定為 **Running**，以確保服務未正在執行中。</span><span class="sxs-lookup"><span data-stu-id="99c0b-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="99c0b-119">通用屬性</span><span class="sxs-lookup"><span data-stu-id="99c0b-119">Common properties</span></span>

|<span data-ttu-id="99c0b-120">屬性</span><span class="sxs-lookup"><span data-stu-id="99c0b-120">Property</span></span> |<span data-ttu-id="99c0b-121">描述</span><span class="sxs-lookup"><span data-stu-id="99c0b-121">Description</span></span> |
|---|---|
|<span data-ttu-id="99c0b-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="99c0b-122">DependsOn</span></span> |<span data-ttu-id="99c0b-123">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="99c0b-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="99c0b-124">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="99c0b-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="99c0b-125">其他資訊</span><span class="sxs-lookup"><span data-stu-id="99c0b-125">Additional Information</span></span>

<span data-ttu-id="99c0b-126">如果服務定義或服務的指令碼不存在，**nxService** 資源將不會建立服務定義或服務的指令碼。</span><span class="sxs-lookup"><span data-stu-id="99c0b-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="99c0b-127">您可以使用 PowerShell 預期狀態設定 **nxFile** 資源資源，以管理服務定義檔或指令碼的內容是否存在。</span><span class="sxs-lookup"><span data-stu-id="99c0b-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="99c0b-128">範例</span><span class="sxs-lookup"><span data-stu-id="99c0b-128">Example</span></span>

<span data-ttu-id="99c0b-129">下列範例顯示 'httpd' 服務設定 (適用於 Apache HTTP Server)，且已向 **SystemD** 服務控制站登錄。</span><span class="sxs-lookup"><span data-stu-id="99c0b-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```