---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxUser 資源
ms.openlocfilehash: ca77bcd1f23a78ddb9e2ac988e4aadfec504bbbe
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="c5c2d-103">DSC for Linux nxUser 資源</span><span class="sxs-lookup"><span data-stu-id="c5c2d-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="c5c2d-104">PowerShell 預期狀態設定 (DSC) 的 **nxUser** 資源會提供一個機制，在 Linux 節點管理本機使用者。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5c2d-105">語法</span><span class="sxs-lookup"><span data-stu-id="c5c2d-105">Syntax</span></span>

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c5c2d-106">Properties</span><span class="sxs-lookup"><span data-stu-id="c5c2d-106">Properties</span></span>

|  <span data-ttu-id="c5c2d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c5c2d-107">Property</span></span> |  <span data-ttu-id="c5c2d-108">指出您要確保其特定狀態的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
| <span data-ttu-id="c5c2d-109">UserName</span><span class="sxs-lookup"><span data-stu-id="c5c2d-109">UserName</span></span>| <span data-ttu-id="c5c2d-110">指定您要確認檔案或目錄狀態的位置。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="c5c2d-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="c5c2d-111">Ensure</span></span>| <span data-ttu-id="c5c2d-112">指定帳戶是否存在。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-112">Specifies whether the account exists.</span></span> <span data-ttu-id="c5c2d-113">設定此屬性為 "Present" 以確保帳戶存在，而設為 "Absent" 可確保帳戶不存在。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-113">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="c5c2d-114">FullName</span><span class="sxs-lookup"><span data-stu-id="c5c2d-114">FullName</span></span>| <span data-ttu-id="c5c2d-115">字串，包含要用於使用者帳戶的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-115">A string that contains the full name to use for the user account.</span></span>|
| <span data-ttu-id="c5c2d-116">描述</span><span class="sxs-lookup"><span data-stu-id="c5c2d-116">Description</span></span>| <span data-ttu-id="c5c2d-117">使用者帳戶的描述。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-117">The description for the user account.</span></span>|
| <span data-ttu-id="c5c2d-118">密碼</span><span class="sxs-lookup"><span data-stu-id="c5c2d-118">Password</span></span>| <span data-ttu-id="c5c2d-119">Linux 電腦適當表單的使用者密碼雜湊。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-119">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="c5c2d-120">一般而言，這是「加鹽」過 (在密碼任意固定位置插入特定的字串) 的 SHA-256 或 SHA-512 雜湊。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-120">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="c5c2d-121">在 Debian 和 Ubuntu Linux 上，這個值可使用 mkpasswd 命令產生。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-121">On Debian and Ubuntu Linux, this value can be generated with the mkpasswd command.</span></span> <span data-ttu-id="c5c2d-122">針對其他 Linux 散發版本，Python 的 Crypt 程式庫的 crypt 方法可用來產生此雜湊。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-122">For other Linux distros, the crypt method of Python’s Crypt library can be used to generate the hash.</span></span>|
| <span data-ttu-id="c5c2d-123">停用</span><span class="sxs-lookup"><span data-stu-id="c5c2d-123">Disabled</span></span>| <span data-ttu-id="c5c2d-124">指出此帳戶是否啟用。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-124">Indicates whether the account is enabled.</span></span> <span data-ttu-id="c5c2d-125">將此屬性設定為 **$true** 以確保此帳戶已停用，而設定為 **$false** 可確定已啟用。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-125">Set this property to **$true** to ensure that this account is disabled, and set it to **$false** to ensure that it is enabled.</span></span>|
| <span data-ttu-id="c5c2d-126">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="c5c2d-126">PasswordChangeRequired</span></span>| <span data-ttu-id="c5c2d-127">指出使用者是否可以變更密碼。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-127">Indicates whether the user can change the password.</span></span> <span data-ttu-id="c5c2d-128">將此屬性設定為 **$true** 以確保使用者無法變更密碼，而設定為 **$false** 可允許使用者變更密碼。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-128">Set this property to **$true** to ensure that the user cannot change the password, and set it to **$false** to allow the user to change the password.</span></span> <span data-ttu-id="c5c2d-129">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-129">The default value is **$false**.</span></span> <span data-ttu-id="c5c2d-130">如果之前不存在此使用者帳戶，而且正在建立中，才會評估這個屬性。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-130">This property is only evaluated if the user account did not exist previously and is being created.</span></span>|
| <span data-ttu-id="c5c2d-131">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="c5c2d-131">HomeDirectory</span></span>| <span data-ttu-id="c5c2d-132">使用者主目錄。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-132">The home directory for the user.</span></span>|
| <span data-ttu-id="c5c2d-133">GroupID</span><span class="sxs-lookup"><span data-stu-id="c5c2d-133">GroupID</span></span>| <span data-ttu-id="c5c2d-134">使用者主要群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-134">The primary group ID for the user.</span></span>|
| <span data-ttu-id="c5c2d-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c5c2d-135">DependsOn</span></span> | <span data-ttu-id="c5c2d-136">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c5c2d-137">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 "ResourceName"，而它的類型是 "ResourceType"，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-137">For example, if the ID of the resource configuration script block that you want to run first is "ResourceName" and its type is "ResourceType", the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c5c2d-138">範例</span><span class="sxs-lookup"><span data-stu-id="c5c2d-138">Example</span></span>

<span data-ttu-id="c5c2d-139">下列範例會確保使用者 "monuser" 存在，而且是 "DBusers" 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="c5c2d-139">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

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