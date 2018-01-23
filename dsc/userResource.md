---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC 使用者資源"
ms.openlocfilehash: c1b8487d9adc899950d185036ada3a2fa3747417
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="6aa62-103">DSC 使用者資源#</span><span class="sxs-lookup"><span data-stu-id="6aa62-103">DSC User Resource#</span></span>

 
><span data-ttu-id="6aa62-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6aa62-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="6aa62-105">Windows PowerShell 預期狀態設定 (DSC) 的 __User__ 資源，會提供在目標節點管理本機使用者帳戶的機制。</span><span class="sxs-lookup"><span data-stu-id="6aa62-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="6aa62-106">語法##</span><span class="sxs-lookup"><span data-stu-id="6aa62-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="6aa62-107">Properties</span><span class="sxs-lookup"><span data-stu-id="6aa62-107">Properties</span></span>
|  <span data-ttu-id="6aa62-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6aa62-108">Property</span></span>  |  <span data-ttu-id="6aa62-109">描述</span><span class="sxs-lookup"><span data-stu-id="6aa62-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="6aa62-110">UserName</span><span class="sxs-lookup"><span data-stu-id="6aa62-110">UserName</span></span>| <span data-ttu-id="6aa62-111">指出您要確保其特定狀態的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="6aa62-111">Indicates the account name for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="6aa62-112">描述</span><span class="sxs-lookup"><span data-stu-id="6aa62-112">Description</span></span>| <span data-ttu-id="6aa62-113">表示您要使用的使用者帳戶描述。</span><span class="sxs-lookup"><span data-stu-id="6aa62-113">Indicates the description you want to use for the user account.</span></span>| 
| <span data-ttu-id="6aa62-114">停用</span><span class="sxs-lookup"><span data-stu-id="6aa62-114">Disabled</span></span>| <span data-ttu-id="6aa62-115">表示帳戶是否啟用。</span><span class="sxs-lookup"><span data-stu-id="6aa62-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="6aa62-116">將此屬性設定為 __$true__ 以確保此帳戶已停用，而設定為 __$false__ 可確定已啟用。</span><span class="sxs-lookup"><span data-stu-id="6aa62-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="6aa62-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="6aa62-117">Ensure</span></span>| <span data-ttu-id="6aa62-118">表示帳戶是否存在。</span><span class="sxs-lookup"><span data-stu-id="6aa62-118">Indicates if the account exists.</span></span> <span data-ttu-id="6aa62-119">設定此屬性為 "Present" 以確保帳戶存在，而設為 "Absent" 可確保帳戶不存在。</span><span class="sxs-lookup"><span data-stu-id="6aa62-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="6aa62-120">FullName</span><span class="sxs-lookup"><span data-stu-id="6aa62-120">FullName</span></span>| <span data-ttu-id="6aa62-121">代表有您要使用的完整使用者帳戶名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="6aa62-121">Represents a string with the full name you want to use for the user account.</span></span>| 
| <span data-ttu-id="6aa62-122">密碼</span><span class="sxs-lookup"><span data-stu-id="6aa62-122">Password</span></span>| <span data-ttu-id="6aa62-123">表示您想要用於這個帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="6aa62-123">Indicates the password you want to use for this account.</span></span> | 
| <span data-ttu-id="6aa62-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="6aa62-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="6aa62-125">表示使用者是否可以變更密碼。</span><span class="sxs-lookup"><span data-stu-id="6aa62-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="6aa62-126">將此屬性設定為 __$true__ 以確保使用者無法變更密碼，而設定為 __$false__ 可允許使用者變更密碼。</span><span class="sxs-lookup"><span data-stu-id="6aa62-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="6aa62-127">預設值為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="6aa62-127">The default value is __$false__.</span></span>| 
| <span data-ttu-id="6aa62-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="6aa62-128">PasswordChangeRequired</span></span>| <span data-ttu-id="6aa62-129">表示使用者是否必須在下次登入時變更密碼。</span><span class="sxs-lookup"><span data-stu-id="6aa62-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="6aa62-130">如果使用者必須變更密碼，請將此屬性設定為 __$true__。</span><span class="sxs-lookup"><span data-stu-id="6aa62-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="6aa62-131">預設值為 __$true__。</span><span class="sxs-lookup"><span data-stu-id="6aa62-131">The default value is __$true__.</span></span>| 
| <span data-ttu-id="6aa62-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="6aa62-132">PasswordNeverExpires</span></span>| <span data-ttu-id="6aa62-133">表示密碼是否會到期。</span><span class="sxs-lookup"><span data-stu-id="6aa62-133">Indicates if the password will expire.</span></span> <span data-ttu-id="6aa62-134">為確保這個帳戶的密碼永遠不會到期，請將這個屬性設定為 __$true__，如果密碼會到期請將它設定為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="6aa62-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="6aa62-135">預設值為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="6aa62-135">The default value is __$false__.</span></span>| 
| <span data-ttu-id="6aa62-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6aa62-136">DependsOn</span></span> | <span data-ttu-id="6aa62-137">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="6aa62-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6aa62-138">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6aa62-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="6aa62-139">範例</span><span class="sxs-lookup"><span data-stu-id="6aa62-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

