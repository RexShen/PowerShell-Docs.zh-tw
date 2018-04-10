---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxGroup 資源
ms.openlocfilehash: 750b7c38a38fb8a7781585a3a7776f832ee62495
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="a26f2-103">DSC for Linux nxGroup 資源</span><span class="sxs-lookup"><span data-stu-id="a26f2-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="a26f2-104">PowerShell 預期狀態設定 (DSC) 的 **nxGroup** 資源會提供一個機制，在 Linux 節點管理本機群組。</span><span class="sxs-lookup"><span data-stu-id="a26f2-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a26f2-105">語法</span><span class="sxs-lookup"><span data-stu-id="a26f2-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="a26f2-106">Properties</span><span class="sxs-lookup"><span data-stu-id="a26f2-106">Properties</span></span>

|  <span data-ttu-id="a26f2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a26f2-107">Property</span></span> |  <span data-ttu-id="a26f2-108">描述</span><span class="sxs-lookup"><span data-stu-id="a26f2-108">Description</span></span> |
|---|---|
| <span data-ttu-id="a26f2-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="a26f2-109">GroupName</span></span>| <span data-ttu-id="a26f2-110">指出您要確保其特定狀態的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="a26f2-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="a26f2-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="a26f2-111">Ensure</span></span>| <span data-ttu-id="a26f2-112">決定是否要檢查群組存在。</span><span class="sxs-lookup"><span data-stu-id="a26f2-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="a26f2-113">將此屬性設定為 "Present" 以確保群組存在。</span><span class="sxs-lookup"><span data-stu-id="a26f2-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="a26f2-114">設為 "Absent" 以確保此群組不存在。</span><span class="sxs-lookup"><span data-stu-id="a26f2-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="a26f2-115">預設值為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="a26f2-115">The default value is "Present".</span></span>|
| <span data-ttu-id="a26f2-116">成員</span><span class="sxs-lookup"><span data-stu-id="a26f2-116">Members</span></span>| <span data-ttu-id="a26f2-117">指定組成群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a26f2-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="a26f2-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="a26f2-118">MembersToInclude</span></span>| <span data-ttu-id="a26f2-119">指定您想要確認的使用者是此群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a26f2-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="a26f2-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="a26f2-120">MembersToExclude</span></span>| <span data-ttu-id="a26f2-121">指定您想要確認的使用者不是此群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a26f2-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="a26f2-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="a26f2-122">PreferredGroupID</span></span>| <span data-ttu-id="a26f2-123">如果可能的話，將群組識別碼設定為提供的值。</span><span class="sxs-lookup"><span data-stu-id="a26f2-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="a26f2-124">如果群組識別碼目前正在使用中，就會使用下一個可用的群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="a26f2-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="a26f2-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a26f2-125">DependsOn</span></span> | <span data-ttu-id="a26f2-126">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="a26f2-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a26f2-127">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="a26f2-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="a26f2-128">範例</span><span class="sxs-lookup"><span data-stu-id="a26f2-128">Example</span></span>

<span data-ttu-id="a26f2-129">下列範例會確保使用者 “monuser” 存在，而且是 "DBusers" 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a26f2-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```