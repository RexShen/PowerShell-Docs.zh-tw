---
ms.date: 09/20/2019
ms.topic: reference
title: DSC GroupSet 資源
description: DSC GroupSet 資源
ms.openlocfilehash: a9d1803aca40ac3571d42a5fd762489c03ed274e
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142883"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="217ce-103">DSC GroupSet 資源</span><span class="sxs-lookup"><span data-stu-id="217ce-103">DSC GroupSet Resource</span></span>

> <span data-ttu-id="217ce-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="217ce-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="217ce-105">Windows PowerShell 預期狀態設定 (DSC) 的 **GroupSet** 資源會提供一個機制，在目標節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="217ce-105">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="217ce-106">此資源是為 `GroupName` 參數中指定的每個群組呼叫 [Group 資源](groupResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="217ce-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="217ce-107">當您想要新增及 (或) 移除多個群組的相同成員清單、移除多個群組，或新增具有相同成員清單的多個群組時，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="217ce-107">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="217ce-108">語法</span><span class="sxs-lookup"><span data-stu-id="217ce-108">Syntax</span></span>

```Syntax
GroupSet [string] #ResourceName
{
    GroupName = [string[]]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="217ce-109">屬性</span><span class="sxs-lookup"><span data-stu-id="217ce-109">Properties</span></span>

|<span data-ttu-id="217ce-110">屬性</span><span class="sxs-lookup"><span data-stu-id="217ce-110">Property</span></span> |<span data-ttu-id="217ce-111">描述</span><span class="sxs-lookup"><span data-stu-id="217ce-111">Description</span></span> |
|---|---|
|<span data-ttu-id="217ce-112">GroupName</span><span class="sxs-lookup"><span data-stu-id="217ce-112">GroupName</span></span> |<span data-ttu-id="217ce-113">您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="217ce-113">The names of the groups for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="217ce-114">成員</span><span class="sxs-lookup"><span data-stu-id="217ce-114">Members</span></span> |<span data-ttu-id="217ce-115">您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="217ce-115">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="217ce-116">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="217ce-116">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="217ce-117">如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。</span><span class="sxs-lookup"><span data-stu-id="217ce-117">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="217ce-118">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="217ce-118">Doing so will generate an error.</span></span> |
|<span data-ttu-id="217ce-119">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="217ce-119">MembersToInclude</span></span> |<span data-ttu-id="217ce-120">使用這個屬性將成員新增至群組的現有成員資格。</span><span class="sxs-lookup"><span data-stu-id="217ce-120">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="217ce-121">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="217ce-121">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="217ce-122">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="217ce-122">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="217ce-123">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="217ce-123">Doing so will generate an error.</span></span> |
|<span data-ttu-id="217ce-124">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="217ce-124">MembersToExclude</span></span> |<span data-ttu-id="217ce-125">使用這個屬性從現有的群組成員資格移除成員。</span><span class="sxs-lookup"><span data-stu-id="217ce-125">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="217ce-126">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="217ce-126">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="217ce-127">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="217ce-127">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="217ce-128">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="217ce-128">Doing so will generate an error.</span></span> |
|<span data-ttu-id="217ce-129">認證</span><span class="sxs-lookup"><span data-stu-id="217ce-129">Credential</span></span> |<span data-ttu-id="217ce-130">存取遠端資源時所需的認證。</span><span class="sxs-lookup"><span data-stu-id="217ce-130">The credentials required to access remote resources.</span></span> <span data-ttu-id="217ce-131">此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶新增至群組；否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="217ce-131">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="217ce-132">通用屬性</span><span class="sxs-lookup"><span data-stu-id="217ce-132">Common properties</span></span>

|<span data-ttu-id="217ce-133">屬性</span><span class="sxs-lookup"><span data-stu-id="217ce-133">Property</span></span> |<span data-ttu-id="217ce-134">描述</span><span class="sxs-lookup"><span data-stu-id="217ce-134">Description</span></span> |
|---|---|
|<span data-ttu-id="217ce-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="217ce-135">DependsOn</span></span> |<span data-ttu-id="217ce-136">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="217ce-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="217ce-137">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="217ce-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="217ce-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="217ce-138">Ensure</span></span> |<span data-ttu-id="217ce-139">表示群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="217ce-139">Indicates whether the groups exist.</span></span> <span data-ttu-id="217ce-140">將此屬性設定為 **Absent** 以確保群組不存在。</span><span class="sxs-lookup"><span data-stu-id="217ce-140">Set this property to **Absent** to ensure that the groups do not exist.</span></span> <span data-ttu-id="217ce-141">設定此群組為 **Present** 以確保群組存在。</span><span class="sxs-lookup"><span data-stu-id="217ce-141">Setting it to **Present** ensures that the groups exist.</span></span> <span data-ttu-id="217ce-142">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="217ce-142">The default value is **Present** .</span></span> |
|<span data-ttu-id="217ce-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="217ce-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="217ce-144">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="217ce-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="217ce-145">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="217ce-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="217ce-146">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="217ce-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="217ce-147">範例 1：確定群組存在</span><span class="sxs-lookup"><span data-stu-id="217ce-147">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="217ce-148">下例示範如何確保 "myGroup" 和 "myOtherGroup" 兩個群組會出現。</span><span class="sxs-lookup"><span data-stu-id="217ce-148">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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
> <span data-ttu-id="217ce-149">為求簡潔，本範例使用純文字認證。</span><span class="sxs-lookup"><span data-stu-id="217ce-149">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="217ce-150">如需如何在設定 MOF 檔案中加密認證的相關資訊，請參閱[保護 MOF 檔案](../../../pull-server/secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="217ce-150">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
