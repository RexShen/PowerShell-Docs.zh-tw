---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxService 資源
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047125"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="1a07e-103">DSC for Linux nxService 資源</span><span class="sxs-lookup"><span data-stu-id="1a07e-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="1a07e-104">PowerShell 預期狀態設定 (DSC) 的 **nxService** 資源會提供一個機制，在 Linux 節點管理服務。</span><span class="sxs-lookup"><span data-stu-id="1a07e-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a07e-105">語法</span><span class="sxs-lookup"><span data-stu-id="1a07e-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="1a07e-106">Properties</span><span class="sxs-lookup"><span data-stu-id="1a07e-106">Properties</span></span>

| <span data-ttu-id="1a07e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1a07e-107">Property</span></span> | <span data-ttu-id="1a07e-108">描述</span><span class="sxs-lookup"><span data-stu-id="1a07e-108">Description</span></span> |
|---|---|
| <span data-ttu-id="1a07e-109">名稱</span><span class="sxs-lookup"><span data-stu-id="1a07e-109">Name</span></span>| <span data-ttu-id="1a07e-110">要設定的服務/精靈名稱。</span><span class="sxs-lookup"><span data-stu-id="1a07e-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="1a07e-111">控制器</span><span class="sxs-lookup"><span data-stu-id="1a07e-111">Controller</span></span>| <span data-ttu-id="1a07e-112">設定服務時所要使用的服務控制站類型。</span><span class="sxs-lookup"><span data-stu-id="1a07e-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="1a07e-113">啟用</span><span class="sxs-lookup"><span data-stu-id="1a07e-113">Enabled</span></span>| <span data-ttu-id="1a07e-114">指出是否在開機時啟動服務。</span><span class="sxs-lookup"><span data-stu-id="1a07e-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="1a07e-115">State</span><span class="sxs-lookup"><span data-stu-id="1a07e-115">State</span></span>| <span data-ttu-id="1a07e-116">表示服務是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="1a07e-116">Indicates whether the service is running.</span></span> <span data-ttu-id="1a07e-117">設定此屬性為 "Stopped"，以確保服務未在執行中。</span><span class="sxs-lookup"><span data-stu-id="1a07e-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="1a07e-118">設定為 "Running"，以確保服務未在執行中。</span><span class="sxs-lookup"><span data-stu-id="1a07e-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="1a07e-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1a07e-119">DependsOn</span></span> | <span data-ttu-id="1a07e-120">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="1a07e-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1a07e-121">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1a07e-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="1a07e-122">其他資訊</span><span class="sxs-lookup"><span data-stu-id="1a07e-122">Additional Information</span></span>

<span data-ttu-id="1a07e-123">如果服務定義或服務的指令碼不存在，**nxService** 資源將不會建立服務定義或服務的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1a07e-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="1a07e-124">您可以使用 PowerShell 預期狀態設定 **nxFile** 資源資源，以管理服務定義檔或指令碼的內容是否存在。</span><span class="sxs-lookup"><span data-stu-id="1a07e-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="1a07e-125">範例</span><span class="sxs-lookup"><span data-stu-id="1a07e-125">Example</span></span>

<span data-ttu-id="1a07e-126">下列範例顯示 'httpd' 服務設定 (適用於 Apache HTTP Server)，且已向 **SystemD** 服務控制站登錄。</span><span class="sxs-lookup"><span data-stu-id="1a07e-126">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```