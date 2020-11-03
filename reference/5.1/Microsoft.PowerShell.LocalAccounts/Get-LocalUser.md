---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202231"
---
# <span data-ttu-id="30c6c-103">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-103">Get-LocalUser</span></span>

## <span data-ttu-id="30c6c-104">概要</span><span class="sxs-lookup"><span data-stu-id="30c6c-104">SYNOPSIS</span></span>
<span data-ttu-id="30c6c-105">取得本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-105">Gets local user accounts.</span></span>

## <span data-ttu-id="30c6c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30c6c-106">SYNTAX</span></span>

### <span data-ttu-id="30c6c-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="30c6c-107">Default (Default)</span></span>

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="30c6c-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="30c6c-108">SecurityIdentifier</span></span>

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="30c6c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="30c6c-109">DESCRIPTION</span></span>

<span data-ttu-id="30c6c-110">此 `Get-LocalUser` Cmdlet 會取得本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-110">The `Get-LocalUser` cmdlet gets local user accounts.</span></span> <span data-ttu-id="30c6c-111">此 Cmdlet 會取得預設的內建使用者帳戶、您建立的本機使用者帳戶，以及您連線到 Microsoft 帳戶的本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-111">This cmdlet gets default built-in user accounts, local user accounts that you created, and local accounts that you connected to Microsoft accounts.</span></span>

> [!NOTE]
> <span data-ttu-id="30c6c-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="30c6c-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="30c6c-113">範例</span><span class="sxs-lookup"><span data-stu-id="30c6c-113">EXAMPLES</span></span>

### <span data-ttu-id="30c6c-114">範例1：使用帳戶的名稱取得帳戶</span><span class="sxs-lookup"><span data-stu-id="30c6c-114">Example 1: Get an account by using its name</span></span>

<span data-ttu-id="30c6c-115">這個範例會取得名為 AdminContoso02 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-115">This example gets a user account named AdminContoso02.</span></span>

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### <span data-ttu-id="30c6c-116">範例2：取得連接到 Microsoft 帳戶的帳戶</span><span class="sxs-lookup"><span data-stu-id="30c6c-116">Example 2: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="30c6c-117">這個範例會取得連接到 Microsoft 帳戶的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-117">This example gets a user account that is connected to a Microsoft account.</span></span> <span data-ttu-id="30c6c-118">此範例會在 Outlook.com 上使用帳戶使用者名稱的預留位置值。</span><span class="sxs-lookup"><span data-stu-id="30c6c-118">This example uses a placeholder value for the username of an account at Outlook.com.</span></span>

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### <span data-ttu-id="30c6c-119">範例3：取得連接到 Microsoft 帳戶的帳戶</span><span class="sxs-lookup"><span data-stu-id="30c6c-119">Example 3: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="30c6c-120">這個範例會取得具有指定之 SID 的本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-120">This example gets a local user account that has the specified SID.</span></span>

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## <span data-ttu-id="30c6c-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30c6c-121">PARAMETERS</span></span>

### <span data-ttu-id="30c6c-122">-Name</span><span class="sxs-lookup"><span data-stu-id="30c6c-122">-Name</span></span>

<span data-ttu-id="30c6c-123">指定此 Cmdlet 取得之使用者帳戶名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="30c6c-123">Specifies an array of names of user accounts that this cmdlet gets.</span></span> <span data-ttu-id="30c6c-124">您可以使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="30c6c-124">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="30c6c-125">-SID</span><span class="sxs-lookup"><span data-stu-id="30c6c-125">-SID</span></span>

<span data-ttu-id="30c6c-126">指定此 Cmdlet 取得之使用者帳戶 (Sid) 的安全識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="30c6c-126">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="30c6c-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30c6c-127">CommonParameters</span></span>

<span data-ttu-id="30c6c-128">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="30c6c-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30c6c-129">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="30c6c-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30c6c-130">輸入</span><span class="sxs-lookup"><span data-stu-id="30c6c-130">INPUTS</span></span>

### <span data-ttu-id="30c6c-131">System.string、SecurityIdentifier、system.object</span><span class="sxs-lookup"><span data-stu-id="30c6c-131">System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="30c6c-132">您可以使用管線將字串或 SID 傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c6c-132">You can pipe a string or SID to this cmdlet.</span></span>

## <span data-ttu-id="30c6c-133">輸出</span><span class="sxs-lookup"><span data-stu-id="30c6c-133">OUTPUTS</span></span>

### <span data-ttu-id="30c6c-134">SecurityAccountsManager. LocalUser []</span><span class="sxs-lookup"><span data-stu-id="30c6c-134">System.Management.Automation.SecurityAccountsManager.LocalUser[]</span></span>

<span data-ttu-id="30c6c-135">此 Cmdlet 會傳回本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30c6c-135">This cmdlet returns local user accounts.</span></span>

## <span data-ttu-id="30c6c-136">注意</span><span class="sxs-lookup"><span data-stu-id="30c6c-136">NOTES</span></span>

<span data-ttu-id="30c6c-137">**LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件上的 **PrincipalSource** 屬性會描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="30c6c-137">The **PrincipalSource** property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects describes the source of the object.</span></span> <span data-ttu-id="30c6c-138">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="30c6c-138">The possible sources are as follows:</span></span>

- <span data-ttu-id="30c6c-139">本機</span><span class="sxs-lookup"><span data-stu-id="30c6c-139">Local</span></span>
- <span data-ttu-id="30c6c-140">Active Directory</span><span class="sxs-lookup"><span data-stu-id="30c6c-140">Active Directory</span></span>
- <span data-ttu-id="30c6c-141">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="30c6c-141">Azure Active Directory group</span></span>
- <span data-ttu-id="30c6c-142">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="30c6c-142">Microsoft Account</span></span>

<span data-ttu-id="30c6c-143">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="30c6c-143">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="30c6c-144">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="30c6c-144">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="30c6c-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="30c6c-145">RELATED LINKS</span></span>

[<span data-ttu-id="30c6c-146">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-146">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="30c6c-147">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-147">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="30c6c-148">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-148">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="30c6c-149">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-149">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="30c6c-150">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-150">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="30c6c-151">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="30c6c-151">Set-LocalUser</span></span>](Set-LocalUser.md)
