---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC 使用者資源
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953005"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="5e209-103">DSC 使用者資源</span><span class="sxs-lookup"><span data-stu-id="5e209-103">DSC User Resource</span></span>

> <span data-ttu-id="5e209-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="5e209-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="5e209-105">Windows PowerShell 預期狀態設定 (DSC) 的 **User** 資源，會提供在目標節點管理本機使用者帳戶的機制。</span><span class="sxs-lookup"><span data-stu-id="5e209-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e209-106">語法</span><span class="sxs-lookup"><span data-stu-id="5e209-106">Syntax</span></span>

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="5e209-107">Properties</span><span class="sxs-lookup"><span data-stu-id="5e209-107">Properties</span></span>

|<span data-ttu-id="5e209-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5e209-108">Property</span></span> |<span data-ttu-id="5e209-109">描述</span><span class="sxs-lookup"><span data-stu-id="5e209-109">Description</span></span> |
|---|---|
|<span data-ttu-id="5e209-110">UserName</span><span class="sxs-lookup"><span data-stu-id="5e209-110">UserName</span></span> |<span data-ttu-id="5e209-111">指出您要確保其特定狀態的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="5e209-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="5e209-112">描述</span><span class="sxs-lookup"><span data-stu-id="5e209-112">Description</span></span> |<span data-ttu-id="5e209-113">表示您要使用的使用者帳戶描述。</span><span class="sxs-lookup"><span data-stu-id="5e209-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="5e209-114">停用</span><span class="sxs-lookup"><span data-stu-id="5e209-114">Disabled</span></span> |<span data-ttu-id="5e209-115">表示帳戶是否啟用。</span><span class="sxs-lookup"><span data-stu-id="5e209-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="5e209-116">將此屬性設定為 `$true` 以確保此帳戶已停用，而將它設定為 `$false` 可確定它已啟用。</span><span class="sxs-lookup"><span data-stu-id="5e209-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="5e209-117">FullName</span><span class="sxs-lookup"><span data-stu-id="5e209-117">FullName</span></span> |<span data-ttu-id="5e209-118">代表有您要使用的完整使用者帳戶名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="5e209-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="5e209-119">密碼</span><span class="sxs-lookup"><span data-stu-id="5e209-119">Password</span></span> |<span data-ttu-id="5e209-120">表示您想要用於這個帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="5e209-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="5e209-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="5e209-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="5e209-122">表示使用者是否可以變更密碼。</span><span class="sxs-lookup"><span data-stu-id="5e209-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="5e209-123">將此屬性設定為 `$true` 以確保使用者無法變更密碼，而將它設定為 `$false` 可允許使用者變更密碼。</span><span class="sxs-lookup"><span data-stu-id="5e209-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="5e209-124">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="5e209-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="5e209-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="5e209-125">PasswordChangeRequired</span></span> |<span data-ttu-id="5e209-126">表示使用者是否必須在下次登入時變更密碼。</span><span class="sxs-lookup"><span data-stu-id="5e209-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="5e209-127">如果使用者必須變更密碼，請將此屬性設定為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="5e209-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="5e209-128">預設值為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="5e209-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="5e209-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="5e209-129">PasswordNeverExpires</span></span> |<span data-ttu-id="5e209-130">表示密碼是否會到期。</span><span class="sxs-lookup"><span data-stu-id="5e209-130">Indicates if the password will expire.</span></span> <span data-ttu-id="5e209-131">為確保這個帳戶的密碼永遠不會到期，請將這個屬性設定為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="5e209-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="5e209-132">如果密碼會到期，則將其設定為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="5e209-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="5e209-133">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="5e209-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="5e209-134">通用屬性</span><span class="sxs-lookup"><span data-stu-id="5e209-134">Common properties</span></span>

|<span data-ttu-id="5e209-135">屬性</span><span class="sxs-lookup"><span data-stu-id="5e209-135">Property</span></span> |<span data-ttu-id="5e209-136">描述</span><span class="sxs-lookup"><span data-stu-id="5e209-136">Description</span></span> |
|---|---|
|<span data-ttu-id="5e209-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5e209-137">DependsOn</span></span> |<span data-ttu-id="5e209-138">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="5e209-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5e209-139">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="5e209-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="5e209-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="5e209-140">Ensure</span></span> |<span data-ttu-id="5e209-141">表示帳戶是否存在。</span><span class="sxs-lookup"><span data-stu-id="5e209-141">Indicates if the account exists.</span></span> <span data-ttu-id="5e209-142">將此屬性設定為 **Present** 以確保帳戶存在，而設定為 **Absent** 可確保帳戶不存在。</span><span class="sxs-lookup"><span data-stu-id="5e209-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="5e209-143">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="5e209-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="5e209-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5e209-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="5e209-145">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="5e209-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="5e209-146">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="5e209-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="5e209-147">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="5e209-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="5e209-148">範例</span><span class="sxs-lookup"><span data-stu-id="5e209-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```