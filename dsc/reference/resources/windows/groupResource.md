---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 群組資源
ms.openlocfilehash: 9894150f6f749fc23efd4ce2b155b18788557d1d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678905"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="e1a57-103">DSC 群組資源</span><span class="sxs-lookup"><span data-stu-id="e1a57-103">DSC Group Resource</span></span>

> <span data-ttu-id="e1a57-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e1a57-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e1a57-105">Windows PowerShell 預期狀態設定 (DSC) 的群組資源會提供一個機制，在目標節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="e1a57-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e1a57-106">語法</span><span class="sxs-lookup"><span data-stu-id="e1a57-106">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="e1a57-107">Properties</span><span class="sxs-lookup"><span data-stu-id="e1a57-107">Properties</span></span>

|  <span data-ttu-id="e1a57-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e1a57-108">Property</span></span>  |  <span data-ttu-id="e1a57-109">描述</span><span class="sxs-lookup"><span data-stu-id="e1a57-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="e1a57-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="e1a57-110">GroupName</span></span>| <span data-ttu-id="e1a57-111">您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="e1a57-111">The name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="e1a57-112">認證</span><span class="sxs-lookup"><span data-stu-id="e1a57-112">Credential</span></span>| <span data-ttu-id="e1a57-113">存取遠端資源時所需的認證。</span><span class="sxs-lookup"><span data-stu-id="e1a57-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="e1a57-114">**注意**：此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶加入群組；否則，在目標節點上執行設定時會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1a57-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
| <span data-ttu-id="e1a57-115">描述</span><span class="sxs-lookup"><span data-stu-id="e1a57-115">Description</span></span>| <span data-ttu-id="e1a57-116">群組的描述。</span><span class="sxs-lookup"><span data-stu-id="e1a57-116">The description of the group.</span></span>|
| <span data-ttu-id="e1a57-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="e1a57-117">Ensure</span></span>| <span data-ttu-id="e1a57-118">指出群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="e1a57-118">Indicates if the group exists.</span></span> <span data-ttu-id="e1a57-119">設定此屬性為 "Absent" 以確保群組不存在。</span><span class="sxs-lookup"><span data-stu-id="e1a57-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="e1a57-120">設定此群組為 "Present" (預設值)，可確保此群組存在。</span><span class="sxs-lookup"><span data-stu-id="e1a57-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>|
| <span data-ttu-id="e1a57-121">成員</span><span class="sxs-lookup"><span data-stu-id="e1a57-121">Members</span></span>| <span data-ttu-id="e1a57-122">您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="e1a57-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="e1a57-123">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="e1a57-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e1a57-124">如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e1a57-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="e1a57-125">這麼做會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1a57-125">Doing so generates an error.</span></span>|
| <span data-ttu-id="e1a57-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="e1a57-126">MembersToExclude</span></span>| <span data-ttu-id="e1a57-127">使用這個屬性從群組的現有成員資格移除成員。</span><span class="sxs-lookup"><span data-stu-id="e1a57-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="e1a57-128">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="e1a57-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e1a57-129">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e1a57-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e1a57-130">這麼做會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1a57-130">Doing so generates an error.</span></span>|
| <span data-ttu-id="e1a57-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="e1a57-131">MembersToInclude</span></span>| <span data-ttu-id="e1a57-132">使用這個屬性將成員新增至群組的現有成員資格。</span><span class="sxs-lookup"><span data-stu-id="e1a57-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="e1a57-133">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="e1a57-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="e1a57-134">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e1a57-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="e1a57-135">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1a57-135">Doing so will generate an error.</span></span>|
| <span data-ttu-id="e1a57-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e1a57-136">DependsOn</span></span> | <span data-ttu-id="e1a57-137">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="e1a57-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e1a57-138">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="e1a57-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="e1a57-139">範例 1</span><span class="sxs-lookup"><span data-stu-id="e1a57-139">Example 1</span></span>

<span data-ttu-id="e1a57-140">下列範例示範如何確定名為 "TestGroup" 的群組不存在。</span><span class="sxs-lookup"><span data-stu-id="e1a57-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a><span data-ttu-id="e1a57-141">範例 2</span><span class="sxs-lookup"><span data-stu-id="e1a57-141">Example 2</span></span>

<span data-ttu-id="e1a57-142">下列範例顯示如何將 Active Directory 使用者以多電腦實驗室組建 (已經在其內使用本機系統管理員帳戶的 PSCredential) 的一部分，加入本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="e1a57-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span>
<span data-ttu-id="e1a57-143">因為這也會用於網域系統管理員帳戶 (在網域升級之後)，所以我們需要將此現有的 PSCredential 轉換為適用於網域的認證。</span><span class="sxs-lookup"><span data-stu-id="e1a57-143">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span>
<span data-ttu-id="e1a57-144">之後，我們便可將網域使用者新增到成員伺服器上的本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="e1a57-144">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

## <a name="example-3"></a><span data-ttu-id="e1a57-145">範例 3</span><span class="sxs-lookup"><span data-stu-id="e1a57-145">Example 3</span></span>

<span data-ttu-id="e1a57-146">下列範例示範如何確定伺服器 TigerTeamSource.Contoso.Com 上的本機群組 TigerTeamAdmins 不包含特定的網域帳戶 Contoso\JerryG。</span><span class="sxs-lookup"><span data-stu-id="e1a57-146">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSrouce {
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