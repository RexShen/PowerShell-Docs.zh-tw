---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC 群組資源"
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="b7cd7-103">DSC 群組資源</span><span class="sxs-lookup"><span data-stu-id="b7cd7-103">DSC Group Resource</span></span>

> <span data-ttu-id="b7cd7-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b7cd7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b7cd7-105">Windows PowerShell 預期狀態設定 (DSC) 的群組資源會提供一個機制，在目標節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7cd7-106">語法</span><span class="sxs-lookup"><span data-stu-id="b7cd7-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="b7cd7-107">[內容]</span><span class="sxs-lookup"><span data-stu-id="b7cd7-107">Properties</span></span>

|  <span data-ttu-id="b7cd7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b7cd7-108">Property</span></span>  |  <span data-ttu-id="b7cd7-109">描述</span><span class="sxs-lookup"><span data-stu-id="b7cd7-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="b7cd7-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="b7cd7-110">GroupName</span></span>| <span data-ttu-id="b7cd7-111">您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="b7cd7-112">認證</span><span class="sxs-lookup"><span data-stu-id="b7cd7-112">Credential</span></span>| <span data-ttu-id="b7cd7-113">存取遠端資源時所需的認證。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="b7cd7-114">**注意**：此帳戶必須具有適當的 Active Directory 權限，藉此將所有非本機帳戶加入群組；否則，在目標節點上執行設定時會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="b7cd7-115">描述</span><span class="sxs-lookup"><span data-stu-id="b7cd7-115">Description</span></span>| <span data-ttu-id="b7cd7-116">群組的描述。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-116">The description of the group.</span></span>| 
| <span data-ttu-id="b7cd7-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="b7cd7-117">Ensure</span></span>| <span data-ttu-id="b7cd7-118">指出群組是否存在。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-118">Indicates if the group exists.</span></span> <span data-ttu-id="b7cd7-119">設定此屬性為 "Absent" 以確保群組不存在。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="b7cd7-120">設定此群組為 "Present" (預設值)，可確保此群組存在。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="b7cd7-121">成員</span><span class="sxs-lookup"><span data-stu-id="b7cd7-121">Members</span></span>| <span data-ttu-id="b7cd7-122">您可以使用這個屬性，以指定的成員來取代目前的群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="b7cd7-123">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="b7cd7-124">如果您在設定中設定這個屬性，請勿使用 **MembersToExclude** 或 **MembersToInclude** 屬性。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="b7cd7-125">這麼做會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="b7cd7-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="b7cd7-126">MembersToExclude</span></span>| <span data-ttu-id="b7cd7-127">使用這個屬性從群組的現有成員資格移除成員。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="b7cd7-128">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="b7cd7-129">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="b7cd7-130">這麼做會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="b7cd7-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="b7cd7-131">MembersToInclude</span></span>| <span data-ttu-id="b7cd7-132">使用這個屬性將成員新增至群組的現有成員資格。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="b7cd7-133">這個屬性值為字串陣列，格式為 *Domain*\\*UserName*。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="b7cd7-134">如果您在設定中設定這個屬性，請勿使用 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="b7cd7-135">這樣會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="b7cd7-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b7cd7-136">DependsOn</span></span> | <span data-ttu-id="b7cd7-137">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b7cd7-138">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="b7cd7-139">範例 1</span><span class="sxs-lookup"><span data-stu-id="b7cd7-139">Example 1</span></span>

<span data-ttu-id="b7cd7-140">下列範例示範如何確定名為 "TestGroup" 的群組不存在。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="b7cd7-141">範例 2</span><span class="sxs-lookup"><span data-stu-id="b7cd7-141">Example 2</span></span>
<span data-ttu-id="b7cd7-142">下列範例顯示如何將 Active Directory 使用者以多電腦實驗室組建 (已經在其內使用本機系統管理員帳戶的 PSCredential) 的一部分，加入本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="b7cd7-143">在網域升級之後，其也會用於網域系統管理員帳戶，然後我們需要將此現有的 PSCredential 轉換為網域能記住的認證，我們如此才可將網域使用者加入成員伺服器上的本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

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

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="b7cd7-144">範例 3</span><span class="sxs-lookup"><span data-stu-id="b7cd7-144">Example 3</span></span>
<span data-ttu-id="b7cd7-145">下列範例示範如何確定伺服器 TigerTeamSource.Contoso.Com 上的本機群組 TigerTeamAdmins 不包含特定的網域帳戶 Contoso\JerryG。</span><span class="sxs-lookup"><span data-stu-id="b7cd7-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

