---
ms.date: 09/20/2019
ms.topic: reference
title: DSC Service 資源
description: DSC Service 資源
ms.openlocfilehash: 24121688bc46dcef70e3751d243d140fb7fcc7c9
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142619"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="84ee9-103">DSC Service 資源</span><span class="sxs-lookup"><span data-stu-id="84ee9-103">DSC Service Resource</span></span>

> <span data-ttu-id="84ee9-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="84ee9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="84ee9-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Service** 資源提供了管理目標節點服務的機制。</span><span class="sxs-lookup"><span data-stu-id="84ee9-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="84ee9-106">語法</span><span class="sxs-lookup"><span data-stu-id="84ee9-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="84ee9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="84ee9-107">Properties</span></span>

|<span data-ttu-id="84ee9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="84ee9-108">Property</span></span> |<span data-ttu-id="84ee9-109">描述</span><span class="sxs-lookup"><span data-stu-id="84ee9-109">Description</span></span> |
|---|---|
|<span data-ttu-id="84ee9-110">名稱</span><span class="sxs-lookup"><span data-stu-id="84ee9-110">Name</span></span> |<span data-ttu-id="84ee9-111">表示服務名稱。</span><span class="sxs-lookup"><span data-stu-id="84ee9-111">Indicates the service name.</span></span> <span data-ttu-id="84ee9-112">請注意，有時候和顯示名稱不同。</span><span class="sxs-lookup"><span data-stu-id="84ee9-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="84ee9-113">您可以使用 `Get-Service` Cmdlet 取得服務清單及其目前狀態。</span><span class="sxs-lookup"><span data-stu-id="84ee9-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="84ee9-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="84ee9-114">BuiltInAccount</span></span> |<span data-ttu-id="84ee9-115">表示用於服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="84ee9-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="84ee9-116">這個屬性所允許的值為： **LocalService** 、 **LocalSystem** 和 **NetworkService** 。</span><span class="sxs-lookup"><span data-stu-id="84ee9-116">The values that are allowed for this property are: **LocalService** , **LocalSystem** , and **NetworkService** .</span></span> |
|<span data-ttu-id="84ee9-117">認證</span><span class="sxs-lookup"><span data-stu-id="84ee9-117">Credential</span></span> |<span data-ttu-id="84ee9-118">表示執行服務的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="84ee9-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="84ee9-119">這個屬性與 **BuiltinAccount** 屬性不能同時使用。</span><span class="sxs-lookup"><span data-stu-id="84ee9-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="84ee9-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="84ee9-120">StartupType</span></span> |<span data-ttu-id="84ee9-121">表示服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="84ee9-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="84ee9-122">這個屬性所允許的值為： **Automatic** 、 **Disabled** 和 **Manual** 。</span><span class="sxs-lookup"><span data-stu-id="84ee9-122">The values that are allowed for this property are: **Automatic** , **Disabled** , and **Manual** .</span></span> |
|<span data-ttu-id="84ee9-123">State</span><span class="sxs-lookup"><span data-stu-id="84ee9-123">State</span></span> |<span data-ttu-id="84ee9-124">表示您要確保的服務狀態。</span><span class="sxs-lookup"><span data-stu-id="84ee9-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="84ee9-125">值如下： **Running** 或 **Stopped** 。</span><span class="sxs-lookup"><span data-stu-id="84ee9-125">The values are: **Running** or **Stopped** .</span></span> |
|<span data-ttu-id="84ee9-126">相依性</span><span class="sxs-lookup"><span data-stu-id="84ee9-126">Dependencies</span></span> | <span data-ttu-id="84ee9-127">服務應具備的相依性名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="84ee9-127">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="84ee9-128">描述</span><span class="sxs-lookup"><span data-stu-id="84ee9-128">Description</span></span> |<span data-ttu-id="84ee9-129">表示目標服務的描述。</span><span class="sxs-lookup"><span data-stu-id="84ee9-129">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="84ee9-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="84ee9-130">DisplayName</span></span> |<span data-ttu-id="84ee9-131">表示目標服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="84ee9-131">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="84ee9-132">路徑</span><span class="sxs-lookup"><span data-stu-id="84ee9-132">Path</span></span> |<span data-ttu-id="84ee9-133">表示新服務的二進位檔路徑。</span><span class="sxs-lookup"><span data-stu-id="84ee9-133">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="84ee9-134">通用屬性</span><span class="sxs-lookup"><span data-stu-id="84ee9-134">Common properties</span></span>

|<span data-ttu-id="84ee9-135">屬性</span><span class="sxs-lookup"><span data-stu-id="84ee9-135">Property</span></span> |<span data-ttu-id="84ee9-136">描述</span><span class="sxs-lookup"><span data-stu-id="84ee9-136">Description</span></span> |
|---|---|
|<span data-ttu-id="84ee9-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="84ee9-137">DependsOn</span></span> |<span data-ttu-id="84ee9-138">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="84ee9-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="84ee9-139">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="84ee9-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="84ee9-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="84ee9-140">Ensure</span></span> |<span data-ttu-id="84ee9-141">表示系統上是否有目標服務。</span><span class="sxs-lookup"><span data-stu-id="84ee9-141">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="84ee9-142">請將此屬性設定為 **Absent** 以確保目標服務不存在。</span><span class="sxs-lookup"><span data-stu-id="84ee9-142">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="84ee9-143">屬性設定為 **Present** ，可確保目標服務存在。</span><span class="sxs-lookup"><span data-stu-id="84ee9-143">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="84ee9-144">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="84ee9-144">The default value is **Present** .</span></span> |
|<span data-ttu-id="84ee9-145">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="84ee9-145">PsDscRunAsCredential</span></span> |<span data-ttu-id="84ee9-146">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="84ee9-146">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="84ee9-147">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="84ee9-147">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="84ee9-148">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="84ee9-148">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="84ee9-149">範例</span><span class="sxs-lookup"><span data-stu-id="84ee9-149">Example</span></span>

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
