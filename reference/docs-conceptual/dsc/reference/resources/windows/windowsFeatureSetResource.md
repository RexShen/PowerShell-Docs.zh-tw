---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WindowsFeatureSet 資源
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952955"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="1b367-103">DSC WindowsFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="1b367-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="1b367-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1b367-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="1b367-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeatureSet** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。</span><span class="sxs-lookup"><span data-stu-id="1b367-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="1b367-106">此資源是為 **Name** 屬性中所指定每項功能呼叫 [WindowsFeature 資源](windowsfeatureResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="1b367-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="1b367-107">當您想要將多個 Windows 功能設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="1b367-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b367-108">語法</span><span class="sxs-lookup"><span data-stu-id="1b367-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1b367-109">Properties</span><span class="sxs-lookup"><span data-stu-id="1b367-109">Properties</span></span>

|  <span data-ttu-id="1b367-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1b367-110">Property</span></span>  |  <span data-ttu-id="1b367-111">描述</span><span class="sxs-lookup"><span data-stu-id="1b367-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="1b367-112">名稱</span><span class="sxs-lookup"><span data-stu-id="1b367-112">Name</span></span> |<span data-ttu-id="1b367-113">您想要確保新增或移除的角色或功能名稱。</span><span class="sxs-lookup"><span data-stu-id="1b367-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="1b367-114">這與 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) Cmdlet 的 **Name** 屬性相同，且不是角色或功能的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="1b367-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="1b367-115">來源</span><span class="sxs-lookup"><span data-stu-id="1b367-115">Source</span></span> |<span data-ttu-id="1b367-116">如有必要，表示用於安裝的來源檔案位置。</span><span class="sxs-lookup"><span data-stu-id="1b367-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="1b367-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="1b367-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="1b367-118">這個屬性設定為 `$true` 可讓您使用以 **Name** 屬性指定的功能包含所有必要子功能。</span><span class="sxs-lookup"><span data-stu-id="1b367-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="1b367-119">認證</span><span class="sxs-lookup"><span data-stu-id="1b367-119">Credential</span></span> |<span data-ttu-id="1b367-120">用以新增或移除角色或功能的認證。</span><span class="sxs-lookup"><span data-stu-id="1b367-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="1b367-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="1b367-121">LogPath</span></span> |<span data-ttu-id="1b367-122">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="1b367-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1b367-123">通用屬性</span><span class="sxs-lookup"><span data-stu-id="1b367-123">Common properties</span></span>

|<span data-ttu-id="1b367-124">屬性</span><span class="sxs-lookup"><span data-stu-id="1b367-124">Property</span></span> |<span data-ttu-id="1b367-125">描述</span><span class="sxs-lookup"><span data-stu-id="1b367-125">Description</span></span> |
|---|---|
|<span data-ttu-id="1b367-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1b367-126">DependsOn</span></span> |<span data-ttu-id="1b367-127">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="1b367-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1b367-128">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1b367-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1b367-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="1b367-129">Ensure</span></span> |<span data-ttu-id="1b367-130">表示是否已新增角色或功能。</span><span class="sxs-lookup"><span data-stu-id="1b367-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="1b367-131">若要確保新增角色或功能，請將此屬性設定為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="1b367-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="1b367-132">若要確保移除角色或功能，請將此屬性設定為 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="1b367-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="1b367-133">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="1b367-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="1b367-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1b367-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="1b367-135">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="1b367-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1b367-136">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="1b367-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1b367-137">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="1b367-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1b367-138">範例</span><span class="sxs-lookup"><span data-stu-id="1b367-138">Example</span></span>

<span data-ttu-id="1b367-139">下列設定可確保安裝 **Web 伺服器** (IIS) 和 **SMTP 伺服器**功能及其各自的所有子功能。</span><span class="sxs-lookup"><span data-stu-id="1b367-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```