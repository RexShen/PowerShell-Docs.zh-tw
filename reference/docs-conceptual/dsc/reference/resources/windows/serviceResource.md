---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC Service 資源
ms.openlocfilehash: acd0710fb4b131876e3edece15b07cff8e9a8a9e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557000"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="909e1-103">DSC Service 資源</span><span class="sxs-lookup"><span data-stu-id="909e1-103">DSC Service Resource</span></span>

> <span data-ttu-id="909e1-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="909e1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="909e1-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Service** 資源提供了管理目標節點服務的機制。</span><span class="sxs-lookup"><span data-stu-id="909e1-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="909e1-106">語法</span><span class="sxs-lookup"><span data-stu-id="909e1-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="909e1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="909e1-107">Properties</span></span>

|<span data-ttu-id="909e1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="909e1-108">Property</span></span> |<span data-ttu-id="909e1-109">描述</span><span class="sxs-lookup"><span data-stu-id="909e1-109">Description</span></span> |
|---|---|
|<span data-ttu-id="909e1-110">名稱</span><span class="sxs-lookup"><span data-stu-id="909e1-110">Name</span></span> |<span data-ttu-id="909e1-111">表示服務名稱。</span><span class="sxs-lookup"><span data-stu-id="909e1-111">Indicates the service name.</span></span> <span data-ttu-id="909e1-112">請注意，有時候和顯示名稱不同。</span><span class="sxs-lookup"><span data-stu-id="909e1-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="909e1-113">您可以使用 `Get-Service` Cmdlet 取得服務清單及其目前狀態。</span><span class="sxs-lookup"><span data-stu-id="909e1-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="909e1-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="909e1-114">BuiltInAccount</span></span> |<span data-ttu-id="909e1-115">表示用於服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="909e1-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="909e1-116">這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="909e1-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="909e1-117">認證</span><span class="sxs-lookup"><span data-stu-id="909e1-117">Credential</span></span> |<span data-ttu-id="909e1-118">表示執行服務的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="909e1-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="909e1-119">這個屬性與 **BuiltinAccount** 屬性不能同時使用。</span><span class="sxs-lookup"><span data-stu-id="909e1-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="909e1-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="909e1-120">StartupType</span></span> |<span data-ttu-id="909e1-121">表示服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="909e1-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="909e1-122">這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="909e1-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="909e1-123">State</span><span class="sxs-lookup"><span data-stu-id="909e1-123">State</span></span> |<span data-ttu-id="909e1-124">表示您要確保的服務狀態。</span><span class="sxs-lookup"><span data-stu-id="909e1-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="909e1-125">值如下：**Running** 或 **Stopped**。</span><span class="sxs-lookup"><span data-stu-id="909e1-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="909e1-126">描述</span><span class="sxs-lookup"><span data-stu-id="909e1-126">Description</span></span> |<span data-ttu-id="909e1-127">表示目標服務的描述。</span><span class="sxs-lookup"><span data-stu-id="909e1-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="909e1-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="909e1-128">DisplayName</span></span> |<span data-ttu-id="909e1-129">表示目標服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="909e1-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="909e1-130">Path</span><span class="sxs-lookup"><span data-stu-id="909e1-130">Path</span></span> |<span data-ttu-id="909e1-131">表示新服務的二進位檔路徑。</span><span class="sxs-lookup"><span data-stu-id="909e1-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="909e1-132">通用屬性</span><span class="sxs-lookup"><span data-stu-id="909e1-132">Common properties</span></span>

|<span data-ttu-id="909e1-133">屬性</span><span class="sxs-lookup"><span data-stu-id="909e1-133">Property</span></span> |<span data-ttu-id="909e1-134">描述</span><span class="sxs-lookup"><span data-stu-id="909e1-134">Description</span></span> |
|---|---|
|<span data-ttu-id="909e1-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="909e1-135">DependsOn</span></span> |<span data-ttu-id="909e1-136">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="909e1-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="909e1-137">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="909e1-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="909e1-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="909e1-138">Ensure</span></span> |<span data-ttu-id="909e1-139">表示系統上是否有目標服務。</span><span class="sxs-lookup"><span data-stu-id="909e1-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="909e1-140">請將此屬性設定為**Absent** 以確保目標服務不存在。</span><span class="sxs-lookup"><span data-stu-id="909e1-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="909e1-141">屬性設定為 **Present**，可確保目標服務存在。</span><span class="sxs-lookup"><span data-stu-id="909e1-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="909e1-142">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="909e1-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="909e1-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="909e1-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="909e1-144">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="909e1-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="909e1-145">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="909e1-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="909e1-146">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="909e1-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="909e1-147">範例</span><span class="sxs-lookup"><span data-stu-id="909e1-147">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
