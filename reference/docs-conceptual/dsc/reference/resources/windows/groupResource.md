---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC 群組資源
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954655"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="4e6cd-103">DSC 群組資源</span><span class="sxs-lookup"><span data-stu-id="4e6cd-103">DSC Group Resource</span></span>

> <span data-ttu-id="4e6cd-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="4e6cd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4e6cd-105">Windows PowerShell Desired State Configuration (DSC) 的**群組**資源會提供一個機制，在目標節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e6cd-106">語法</span><span class="sxs-lookup"><span data-stu-id="4e6cd-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4e6cd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4e6cd-107">Properties</span></span>

|<span data-ttu-id="4e6cd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4e6cd-108">Property</span></span> |<span data-ttu-id="4e6cd-109">描述</span><span class="sxs-lookup"><span data-stu-id="4e6cd-109">Description</span></span> |
|---|---|
|<span data-ttu-id="4e6cd-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="4e6cd-110">GroupName</span></span> |<span data-ttu-id="4e6cd-111">您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="4e6cd-112">認證</span><span class="sxs-lookup"><span data-stu-id="4e6cd-112">Credential</span></span> |<span data-ttu-id="4e6cd-113">存取遠端資源時所需的認證。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="4e6cd-114">此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶新增至群組；否則，在目標節點上執行設定時會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="4e6cd-115">描述</span><span class="sxs-lookup"><span data-stu-id="4e6cd-115">Description</span></span> |<span data-ttu-id="4e6cd-116">群組的描述。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-116">The description of the group.</span></span> |
|<span data-ttu-id="4e6cd-117">成員</span><span class="sxs-lookup"><span data-stu-id="4e6cd-117">Members</span></span> |<span data-ttu-id="4e6cd-118">您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="4e6cd-119">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="4e6cd-120">如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="4e6cd-121">這麼做會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="4e6cd-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="4e6cd-122">MembersToExclude</span></span> |<span data-ttu-id="4e6cd-123">使用這個屬性從群組的現有成員資格移除成員。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="4e6cd-124">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="4e6cd-125">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4e6cd-126">這麼做會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="4e6cd-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="4e6cd-127">MembersToInclude</span></span> |<span data-ttu-id="4e6cd-128">使用這個屬性將成員新增至群組的現有成員資格。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="4e6cd-129">這個屬性值為字串陣列，格式為 `Domain\UserName`。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="4e6cd-130">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="4e6cd-131">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4e6cd-132">通用屬性</span><span class="sxs-lookup"><span data-stu-id="4e6cd-132">Common properties</span></span>

|<span data-ttu-id="4e6cd-133">屬性</span><span class="sxs-lookup"><span data-stu-id="4e6cd-133">Property</span></span> |<span data-ttu-id="4e6cd-134">描述</span><span class="sxs-lookup"><span data-stu-id="4e6cd-134">Description</span></span> |
|---|---|
|<span data-ttu-id="4e6cd-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4e6cd-135">DependsOn</span></span> |<span data-ttu-id="4e6cd-136">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4e6cd-137">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4e6cd-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="4e6cd-138">Ensure</span></span> |<span data-ttu-id="4e6cd-139">指出群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-139">Indicates if the group exists.</span></span> <span data-ttu-id="4e6cd-140">將此屬性設定為 **Absent** 以確保群組不存在。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="4e6cd-141">設定此群組為 **Present** 以確保此群組存在。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="4e6cd-142">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="4e6cd-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4e6cd-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="4e6cd-144">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4e6cd-145">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4e6cd-146">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="4e6cd-147">範例 1：確定群組不存在</span><span class="sxs-lookup"><span data-stu-id="4e6cd-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="4e6cd-148">下列範例示範如何確定名為 "TestGroup" 的群組不存在。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="4e6cd-149">範例 2：將網域使用者新增至本機群組</span><span class="sxs-lookup"><span data-stu-id="4e6cd-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="4e6cd-150">下列範例顯示如何將 Active Directory 使用者新增至本機系統管理員群組，成為已使用本機系統管理員帳戶 PSCredential 之多電腦實驗室組建的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="4e6cd-151">因為這也會用於網域系統管理員帳戶 (在網域升級之後)，所以我們需要將此現有的 PSCredential 轉換為適用於網域的認證。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="4e6cd-152">之後，我們便可將網域使用者新增到成員伺服器上的本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="4e6cd-153">範例 3</span><span class="sxs-lookup"><span data-stu-id="4e6cd-153">Example 3</span></span>

<span data-ttu-id="4e6cd-154">下列範例示範如何確定伺服器 TigerTeamSource.Contoso.Com 上的本機群組 TigerTeamAdmins 不包含特定的網域帳戶 Contoso\JerryG。</span><span class="sxs-lookup"><span data-stu-id="4e6cd-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```