---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC Service 資源
ms.openlocfilehash: f936f58ffd00f84d8c6d5d41d93378eaa8db5879
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463579"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="7e7ef-103">DSC Service 資源</span><span class="sxs-lookup"><span data-stu-id="7e7ef-103">DSC Service Resource</span></span>

> <span data-ttu-id="7e7ef-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7e7ef-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7e7ef-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Service** 資源提供了管理目標節點服務的機制。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e7ef-106">語法</span><span class="sxs-lookup"><span data-stu-id="7e7ef-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupTimeout = [uint32]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Ignore | Running | Stopped }  ]
    [ Dependencies = [string[]] ]
    [ Description = [string] ]
    [ DesktopInteract = [boolean]]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ TerminateTimeout = [uint32] ]
}
```

## <a name="properties"></a><span data-ttu-id="7e7ef-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7e7ef-107">Properties</span></span>

|<span data-ttu-id="7e7ef-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7e7ef-108">Property</span></span> |<span data-ttu-id="7e7ef-109">描述</span><span class="sxs-lookup"><span data-stu-id="7e7ef-109">Description</span></span> |
|---|---|
|<span data-ttu-id="7e7ef-110">名稱</span><span class="sxs-lookup"><span data-stu-id="7e7ef-110">Name</span></span> |<span data-ttu-id="7e7ef-111">表示服務名稱。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-111">Indicates the service name.</span></span> <span data-ttu-id="7e7ef-112">請注意，有時候和顯示名稱不同。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="7e7ef-113">您可以使用 `Get-Service` Cmdlet 取得服務清單及其目前狀態。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="7e7ef-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="7e7ef-114">BuiltInAccount</span></span> |<span data-ttu-id="7e7ef-115">表示用於服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="7e7ef-116">這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="7e7ef-117">認證</span><span class="sxs-lookup"><span data-stu-id="7e7ef-117">Credential</span></span> |<span data-ttu-id="7e7ef-118">表示執行服務的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="7e7ef-119">這個屬性與 **BuiltinAccount** 屬性不能同時使用。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="7e7ef-120">StartupTimeout</span><span class="sxs-lookup"><span data-stu-id="7e7ef-120">StartupTimeout</span></span> | <span data-ttu-id="7e7ef-121">等待服務執行的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-121">The time to wait for the service to be running in milliseconds.</span></span>|
|<span data-ttu-id="7e7ef-122">StartupType</span><span class="sxs-lookup"><span data-stu-id="7e7ef-122">StartupType</span></span> |<span data-ttu-id="7e7ef-123">表示服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-123">Indicates the startup type for the service.</span></span> <span data-ttu-id="7e7ef-124">這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-124">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="7e7ef-125">State</span><span class="sxs-lookup"><span data-stu-id="7e7ef-125">State</span></span> |<span data-ttu-id="7e7ef-126">表示您要確保的服務狀態。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-126">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="7e7ef-127">值如下：**Running** 或 **Stopped**。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-127">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="7e7ef-128">TerminateTimeout</span><span class="sxs-lookup"><span data-stu-id="7e7ef-128">TerminateTimeout</span></span> |<span data-ttu-id="7e7ef-129">等待服務停止的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-129">The time to wait for the service to be stopped in milliseconds.</span></span>|
|<span data-ttu-id="7e7ef-130">相依性</span><span class="sxs-lookup"><span data-stu-id="7e7ef-130">Dependencies</span></span> | <span data-ttu-id="7e7ef-131">服務應具備的相依性名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-131">An array of the names of the dependencies the service should have.</span></span> |
|<span data-ttu-id="7e7ef-132">描述</span><span class="sxs-lookup"><span data-stu-id="7e7ef-132">Description</span></span> |<span data-ttu-id="7e7ef-133">表示目標服務的描述。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-133">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="7e7ef-134">DesktopInteract</span><span class="sxs-lookup"><span data-stu-id="7e7ef-134">DesktopInteract</span></span> | <span data-ttu-id="7e7ef-135">指出服務是否應能夠和桌面上的視窗通訊。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-135">Indicates whether or not the service should be able to communicate with a window on the desktop.</span></span> <span data-ttu-id="7e7ef-136">針對不是以 LocalSystem 執行的服務，必須為 false。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-136">Must be false for services not running as LocalSystem.</span></span>|
|<span data-ttu-id="7e7ef-137">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7e7ef-137">DisplayName</span></span> |<span data-ttu-id="7e7ef-138">表示目標服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-138">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="7e7ef-139">路徑</span><span class="sxs-lookup"><span data-stu-id="7e7ef-139">Path</span></span> |<span data-ttu-id="7e7ef-140">表示新服務的二進位檔路徑。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-140">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7e7ef-141">通用屬性</span><span class="sxs-lookup"><span data-stu-id="7e7ef-141">Common properties</span></span>

|<span data-ttu-id="7e7ef-142">屬性</span><span class="sxs-lookup"><span data-stu-id="7e7ef-142">Property</span></span> |<span data-ttu-id="7e7ef-143">描述</span><span class="sxs-lookup"><span data-stu-id="7e7ef-143">Description</span></span> |
|---|---|
|<span data-ttu-id="7e7ef-144">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7e7ef-144">DependsOn</span></span> |<span data-ttu-id="7e7ef-145">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-145">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e7ef-146">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-146">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7e7ef-147">Ensure</span><span class="sxs-lookup"><span data-stu-id="7e7ef-147">Ensure</span></span> |<span data-ttu-id="7e7ef-148">表示系統上是否有目標服務。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-148">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="7e7ef-149">請將此屬性設定為**Absent** 以確保目標服務不存在。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-149">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="7e7ef-150">屬性設定為 **Present**，可確保目標服務存在。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-150">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="7e7ef-151">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-151">The default value is **Present**.</span></span> |
|<span data-ttu-id="7e7ef-152">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7e7ef-152">PsDscRunAsCredential</span></span> |<span data-ttu-id="7e7ef-153">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-153">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7e7ef-154">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-154">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7e7ef-155">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7ef-155">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="7e7ef-156">範例</span><span class="sxs-lookup"><span data-stu-id="7e7ef-156">Example</span></span>

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
