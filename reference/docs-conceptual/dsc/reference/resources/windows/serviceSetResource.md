---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC ServiceSet 資源
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953025"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="2853d-103">DSC ServiceSet 資源</span><span class="sxs-lookup"><span data-stu-id="2853d-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="2853d-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="2853d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="2853d-105">Windows PowerShell 預期狀態設定 (DSC) 的 **ServiceSet** 資源提供了管理目標節點服務的機制。</span><span class="sxs-lookup"><span data-stu-id="2853d-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="2853d-106">此資源是為 **Name** 屬性中所指定每項服務呼叫 [Service 資源](serviceResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="2853d-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="2853d-107">當您想要將多項服務設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="2853d-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="2853d-108">語法</span><span class="sxs-lookup"><span data-stu-id="2853d-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2853d-109">Properties</span><span class="sxs-lookup"><span data-stu-id="2853d-109">Properties</span></span>

|<span data-ttu-id="2853d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2853d-110">Property</span></span> |<span data-ttu-id="2853d-111">描述</span><span class="sxs-lookup"><span data-stu-id="2853d-111">Description</span></span> |
|---|---|
|<span data-ttu-id="2853d-112">名稱</span><span class="sxs-lookup"><span data-stu-id="2853d-112">Name</span></span> |<span data-ttu-id="2853d-113">表示服務名稱。</span><span class="sxs-lookup"><span data-stu-id="2853d-113">Indicates the service names.</span></span> <span data-ttu-id="2853d-114">請注意，有時候和顯示名稱不同。</span><span class="sxs-lookup"><span data-stu-id="2853d-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="2853d-115">您可以使用 `Get-Service` Cmdlet 取得服務清單及其目前狀態。</span><span class="sxs-lookup"><span data-stu-id="2853d-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="2853d-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="2853d-116">StartupType</span></span> |<span data-ttu-id="2853d-117">表示服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="2853d-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="2853d-118">這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="2853d-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="2853d-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="2853d-119">BuiltInAccount</span></span> |<span data-ttu-id="2853d-120">表示用於服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="2853d-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="2853d-121">這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="2853d-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="2853d-122">State</span><span class="sxs-lookup"><span data-stu-id="2853d-122">State</span></span> |<span data-ttu-id="2853d-123">表示您要確保的服務狀態：**Stopped** 或 **Running**。</span><span class="sxs-lookup"><span data-stu-id="2853d-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="2853d-124">認證</span><span class="sxs-lookup"><span data-stu-id="2853d-124">Credential</span></span> |<span data-ttu-id="2853d-125">表示執行服務資源的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="2853d-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="2853d-126">這個屬性與 **BuiltinAccount** 屬性不能同時使用。</span><span class="sxs-lookup"><span data-stu-id="2853d-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2853d-127">通用屬性</span><span class="sxs-lookup"><span data-stu-id="2853d-127">Common properties</span></span>

|<span data-ttu-id="2853d-128">屬性</span><span class="sxs-lookup"><span data-stu-id="2853d-128">Property</span></span> |<span data-ttu-id="2853d-129">描述</span><span class="sxs-lookup"><span data-stu-id="2853d-129">Description</span></span> |
|---|---|
|<span data-ttu-id="2853d-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2853d-130">DependsOn</span></span> |<span data-ttu-id="2853d-131">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="2853d-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2853d-132">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="2853d-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2853d-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="2853d-133">Ensure</span></span> |<span data-ttu-id="2853d-134">表示系統上是否有服務。</span><span class="sxs-lookup"><span data-stu-id="2853d-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="2853d-135">請將此屬性設為 **Absent** 以確保服務不存在。</span><span class="sxs-lookup"><span data-stu-id="2853d-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="2853d-136">屬性設定為 **Present**，可確保目標服務存在。</span><span class="sxs-lookup"><span data-stu-id="2853d-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="2853d-137">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="2853d-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="2853d-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2853d-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="2853d-139">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="2853d-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="2853d-140">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="2853d-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="2853d-141">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="2853d-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="2853d-142">範例</span><span class="sxs-lookup"><span data-stu-id="2853d-142">Example</span></span>

<span data-ttu-id="2853d-143">下列設定會啟動「Windows 音訊」和「遠端桌面服務」服務。</span><span class="sxs-lookup"><span data-stu-id="2853d-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```