---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxGroup 資源
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953205"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="7d3fc-103">DSC for Linux nxGroup 資源</span><span class="sxs-lookup"><span data-stu-id="7d3fc-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="7d3fc-104">PowerShell 預期狀態設定 (DSC) 的 **nxGroup** 資源會提供一個機制，在 Linux 節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d3fc-105">語法</span><span class="sxs-lookup"><span data-stu-id="7d3fc-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="7d3fc-106">Properties</span><span class="sxs-lookup"><span data-stu-id="7d3fc-106">Properties</span></span>

|<span data-ttu-id="7d3fc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7d3fc-107">Property</span></span> |<span data-ttu-id="7d3fc-108">描述</span><span class="sxs-lookup"><span data-stu-id="7d3fc-108">Description</span></span> |
|---|---|
|<span data-ttu-id="7d3fc-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="7d3fc-109">GroupName</span></span> |<span data-ttu-id="7d3fc-110">指出您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="7d3fc-111">成員</span><span class="sxs-lookup"><span data-stu-id="7d3fc-111">Members</span></span> |<span data-ttu-id="7d3fc-112">指定組成群組的成員。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="7d3fc-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="7d3fc-113">MembersToInclude</span></span> |<span data-ttu-id="7d3fc-114">指定您想要確認的使用者是此群組的成員。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="7d3fc-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="7d3fc-115">MembersToExclude</span></span> |<span data-ttu-id="7d3fc-116">指定您想要確認的使用者不是此群組的成員。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="7d3fc-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="7d3fc-117">PreferredGroupID</span></span> |<span data-ttu-id="7d3fc-118">如果可能的話，將群組識別碼設定為提供的值。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="7d3fc-119">如果群組識別碼目前正在使用中，就會使用下一個可用的群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7d3fc-120">通用屬性</span><span class="sxs-lookup"><span data-stu-id="7d3fc-120">Common properties</span></span>

|<span data-ttu-id="7d3fc-121">屬性</span><span class="sxs-lookup"><span data-stu-id="7d3fc-121">Property</span></span> |<span data-ttu-id="7d3fc-122">描述</span><span class="sxs-lookup"><span data-stu-id="7d3fc-122">Description</span></span> |
|---|---|
|<span data-ttu-id="7d3fc-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7d3fc-123">DependsOn</span></span> |<span data-ttu-id="7d3fc-124">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7d3fc-125">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7d3fc-126">Ensure</span><span class="sxs-lookup"><span data-stu-id="7d3fc-126">Ensure</span></span> |<span data-ttu-id="7d3fc-127">決定是否要檢查群組存在。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="7d3fc-128">將此屬性設定為 **Present** 以確保群組存在。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="7d3fc-129">將其設定為 **Absent** 以確保此群組不存在。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="7d3fc-130">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-130">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="7d3fc-131">範例</span><span class="sxs-lookup"><span data-stu-id="7d3fc-131">Example</span></span>

<span data-ttu-id="7d3fc-132">下列範例會確保使用者 'monuser' 存在，而且是 'DBusers' 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```