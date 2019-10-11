---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
description: 提供在目標節點管理本機群組的機制。
title: DSC GroupSet 資源
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953175"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="358c3-104">DSC GroupSet 資源</span><span class="sxs-lookup"><span data-stu-id="358c3-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="358c3-105">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="358c3-105">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="358c3-106">Windows PowerShell 預期狀態設定 (DSC) 的 **GroupSet** 資源會提供一個機制，在目標節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="358c3-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="358c3-107">此資源是為 `GroupName` 參數中指定的每個群組呼叫 [Group 資源](groupResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="358c3-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="358c3-108">當您想要新增及 (或) 移除多個群組的相同成員清單、移除多個群組，或新增具有相同成員清單的多個群組時，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="358c3-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="358c3-109">語法</span><span class="sxs-lookup"><span data-stu-id="358c3-109">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="358c3-110">Properties</span><span class="sxs-lookup"><span data-stu-id="358c3-110">Properties</span></span>

|<span data-ttu-id="358c3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="358c3-111">Property</span></span> |<span data-ttu-id="358c3-112">描述</span><span class="sxs-lookup"><span data-stu-id="358c3-112">Description</span></span> |
|---|---|
|<span data-ttu-id="358c3-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="358c3-113">GroupName</span></span> |<span data-ttu-id="358c3-114">您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="358c3-114">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="358c3-115">成員</span><span class="sxs-lookup"><span data-stu-id="358c3-115">Members</span></span> |<span data-ttu-id="358c3-116">您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="358c3-116">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="358c3-117">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="358c3-117">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="358c3-118">如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。</span><span class="sxs-lookup"><span data-stu-id="358c3-118">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="358c3-119">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="358c3-119">Doing so will generate an error.</span></span> |
|<span data-ttu-id="358c3-120">描述</span><span class="sxs-lookup"><span data-stu-id="358c3-120">Description</span></span> |<span data-ttu-id="358c3-121">群組的描述。</span><span class="sxs-lookup"><span data-stu-id="358c3-121">The description of the group.</span></span> |
|<span data-ttu-id="358c3-122">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="358c3-122">MembersToInclude</span></span> |<span data-ttu-id="358c3-123">使用這個屬性將成員新增至群組的現有成員資格。</span><span class="sxs-lookup"><span data-stu-id="358c3-123">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="358c3-124">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="358c3-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="358c3-125">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="358c3-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="358c3-126">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="358c3-126">Doing so will generate an error.</span></span> |
|<span data-ttu-id="358c3-127">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="358c3-127">MembersToExclude</span></span> |<span data-ttu-id="358c3-128">使用這個屬性從現有的群組成員資格移除成員。</span><span class="sxs-lookup"><span data-stu-id="358c3-128">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="358c3-129">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="358c3-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="358c3-130">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="358c3-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="358c3-131">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="358c3-131">Doing so will generate an error.</span></span> |
|<span data-ttu-id="358c3-132">認證</span><span class="sxs-lookup"><span data-stu-id="358c3-132">Credential</span></span> |<span data-ttu-id="358c3-133">存取遠端資源時所需的認證。</span><span class="sxs-lookup"><span data-stu-id="358c3-133">The credentials required to access remote resources.</span></span> <span data-ttu-id="358c3-134">此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶新增至群組；否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="358c3-134">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="358c3-135">通用屬性</span><span class="sxs-lookup"><span data-stu-id="358c3-135">Common properties</span></span>

|<span data-ttu-id="358c3-136">屬性</span><span class="sxs-lookup"><span data-stu-id="358c3-136">Property</span></span> |<span data-ttu-id="358c3-137">描述</span><span class="sxs-lookup"><span data-stu-id="358c3-137">Description</span></span> |
|---|---|
|<span data-ttu-id="358c3-138">DependsOn</span><span class="sxs-lookup"><span data-stu-id="358c3-138">DependsOn</span></span> |<span data-ttu-id="358c3-139">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="358c3-139">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="358c3-140">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="358c3-140">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="358c3-141">Ensure</span><span class="sxs-lookup"><span data-stu-id="358c3-141">Ensure</span></span> |<span data-ttu-id="358c3-142">表示群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="358c3-142">Indicates whether the groups exist.</span></span> <span data-ttu-id="358c3-143">將此屬性設定為 **Absent** 以確保群組不存在。</span><span class="sxs-lookup"><span data-stu-id="358c3-143">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="358c3-144">設定此群組為 **Present** 以確保群組存在。</span><span class="sxs-lookup"><span data-stu-id="358c3-144">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="358c3-145">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="358c3-145">The default value is **Present**.</span></span> |
|<span data-ttu-id="358c3-146">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="358c3-146">PsDscRunAsCredential</span></span> |<span data-ttu-id="358c3-147">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="358c3-147">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="358c3-148">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="358c3-148">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="358c3-149">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="358c3-149">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="358c3-150">範例 1：確保群組存在</span><span class="sxs-lookup"><span data-stu-id="358c3-150">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="358c3-151">下例示範如何確保 "myGroup" 和 "myOtherGroup" 兩個群組會出現。</span><span class="sxs-lookup"><span data-stu-id="358c3-151">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="358c3-152">為求簡潔，本範例使用純文字認證。</span><span class="sxs-lookup"><span data-stu-id="358c3-152">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="358c3-153">如需如何在設定 MOF 檔案中加密認證的相關資訊，請參閱[保護 MOF 檔案](../../../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="358c3-153">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>