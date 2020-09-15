---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC WindowsFeature 資源
ms.openlocfilehash: b15b267c6898697816b386a381e5a6d59acd492a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464106"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="1ec8d-103">DSC WindowsFeature 資源</span><span class="sxs-lookup"><span data-stu-id="1ec8d-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="1ec8d-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1ec8d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1ec8d-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeature** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ec8d-106">語法</span><span class="sxs-lookup"><span data-stu-id="1ec8d-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1ec8d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1ec8d-107">Properties</span></span>

|<span data-ttu-id="1ec8d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1ec8d-108">Property</span></span> |<span data-ttu-id="1ec8d-109">描述</span><span class="sxs-lookup"><span data-stu-id="1ec8d-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1ec8d-110">名稱</span><span class="sxs-lookup"><span data-stu-id="1ec8d-110">Name</span></span> |<span data-ttu-id="1ec8d-111">表示您想要確保新增或移除的角色或功能名稱。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="1ec8d-112">這與來自 [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) Cmdlet 的 **Name** 屬性相同，不是角色或功能的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="1ec8d-113">認證</span><span class="sxs-lookup"><span data-stu-id="1ec8d-113">Credential</span></span> |<span data-ttu-id="1ec8d-114">表示要用以新增或移除角色或功能的認證。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="1ec8d-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="1ec8d-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="1ec8d-116">將此屬性設定為 `$true` 可讓您使用以 **Name** 屬性指定的功能狀態，來確保所有必要子功能的狀態。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="1ec8d-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="1ec8d-117">LogPath</span></span> |<span data-ttu-id="1ec8d-118">表示要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1ec8d-119">通用屬性</span><span class="sxs-lookup"><span data-stu-id="1ec8d-119">Common properties</span></span>

|<span data-ttu-id="1ec8d-120">屬性</span><span class="sxs-lookup"><span data-stu-id="1ec8d-120">Property</span></span> |<span data-ttu-id="1ec8d-121">描述</span><span class="sxs-lookup"><span data-stu-id="1ec8d-121">Description</span></span> |
|---|---|
|<span data-ttu-id="1ec8d-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1ec8d-122">DependsOn</span></span> |<span data-ttu-id="1ec8d-123">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1ec8d-124">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1ec8d-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="1ec8d-125">Ensure</span></span> |<span data-ttu-id="1ec8d-126">表示角色或功能是否新增。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-126">Indicates if the role or feature is added.</span></span> <span data-ttu-id="1ec8d-127">若要確保新增角色或功能，請將此屬性設定為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-127">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="1ec8d-128">若要確保移除角色或功能，請將此屬性設定為 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-128">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="1ec8d-129">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-129">The default value is **Present**.</span></span> |
|<span data-ttu-id="1ec8d-130">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1ec8d-130">PsDscRunAsCredential</span></span> |<span data-ttu-id="1ec8d-131">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-131">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1ec8d-132">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-132">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1ec8d-133">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec8d-133">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ec8d-134">範例</span><span class="sxs-lookup"><span data-stu-id="1ec8d-134">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```
