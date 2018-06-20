---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
description: 提供在目標節點管理本機群組的機制。
title: DSC GroupSet 資源
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222348"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="24f4b-104">DSC GroupSet 資源</span><span class="sxs-lookup"><span data-stu-id="24f4b-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="24f4b-105">適用於：Windows PowerShell Windows 5.0</span><span class="sxs-lookup"><span data-stu-id="24f4b-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="24f4b-106">Windows PowerShell 預期狀態設定 (DSC) 的 **GroupSet** 資源會提供一個機制，在目標節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="24f4b-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="24f4b-107">此資源是為 `GroupName` 參數中指定的每個群組呼叫 [Group 資源](groupResource.md)的[複合資源](authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="24f4b-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="24f4b-108">當您想要新增及 (或) 移除多個群組的相同成員清單、移除多個群組，或新增具有相同成員清單的多個群組時，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="24f4b-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="24f4b-109">語法##</span><span class="sxs-lookup"><span data-stu-id="24f4b-109">Syntax##</span></span>
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="24f4b-110">Properties</span><span class="sxs-lookup"><span data-stu-id="24f4b-110">Properties</span></span>

|  <span data-ttu-id="24f4b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="24f4b-111">Property</span></span>  |  <span data-ttu-id="24f4b-112">描述</span><span class="sxs-lookup"><span data-stu-id="24f4b-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="24f4b-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="24f4b-113">GroupName</span></span>| <span data-ttu-id="24f4b-114">您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="24f4b-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="24f4b-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="24f4b-115">MembersToExclude</span></span>| <span data-ttu-id="24f4b-116">使用這個屬性從現有的群組成員資格移除成員。</span><span class="sxs-lookup"><span data-stu-id="24f4b-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="24f4b-117">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="24f4b-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="24f4b-118">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="24f4b-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="24f4b-119">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="24f4b-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="24f4b-120">認證</span><span class="sxs-lookup"><span data-stu-id="24f4b-120">Credential</span></span>| <span data-ttu-id="24f4b-121">存取遠端資源時所需的認證。</span><span class="sxs-lookup"><span data-stu-id="24f4b-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="24f4b-122">**注意**：此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶加入群組；否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="24f4b-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="24f4b-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="24f4b-123">Ensure</span></span>| <span data-ttu-id="24f4b-124">表示群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="24f4b-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="24f4b-125">請將此屬性設為 "Absent" 以確保群組不存在。</span><span class="sxs-lookup"><span data-stu-id="24f4b-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="24f4b-126">屬性設定為 "Present" (預設值)，可確保群組存在。</span><span class="sxs-lookup"><span data-stu-id="24f4b-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="24f4b-127">成員</span><span class="sxs-lookup"><span data-stu-id="24f4b-127">Members</span></span>| <span data-ttu-id="24f4b-128">您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="24f4b-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="24f4b-129">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="24f4b-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="24f4b-130">如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。</span><span class="sxs-lookup"><span data-stu-id="24f4b-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="24f4b-131">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="24f4b-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="24f4b-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="24f4b-132">MembersToInclude</span></span>| <span data-ttu-id="24f4b-133">使用這個屬性將成員新增至群組的現有成員資格。</span><span class="sxs-lookup"><span data-stu-id="24f4b-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="24f4b-134">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="24f4b-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="24f4b-135">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="24f4b-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="24f4b-136">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="24f4b-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="24f4b-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="24f4b-137">DependsOn</span></span> | <span data-ttu-id="24f4b-138">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="24f4b-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="24f4b-139">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="24f4b-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="24f4b-140">範例 1</span><span class="sxs-lookup"><span data-stu-id="24f4b-140">Example 1</span></span>

<span data-ttu-id="24f4b-141">下例示範如何確保 "myGroup" 和 "myOtherGroup" 兩個群組會出現。</span><span class="sxs-lookup"><span data-stu-id="24f4b-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

><span data-ttu-id="24f4b-142">**注意︰** 為求簡潔，本例使用純文字認證。</span><span class="sxs-lookup"><span data-stu-id="24f4b-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="24f4b-143">如需如何在設定 MOF 檔案中加密認證的相關資訊，請參閱[保護 MOF 檔案](secureMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="24f4b-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>