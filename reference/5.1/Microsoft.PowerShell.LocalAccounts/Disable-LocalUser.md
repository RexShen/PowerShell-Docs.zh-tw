---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/disable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-LocalUser
ms.openlocfilehash: a62242251da00688d3299c60e4cdae7aae6f581a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202248"
---
# <span data-ttu-id="387f2-103">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-103">Disable-LocalUser</span></span>

## <span data-ttu-id="387f2-104">概要</span><span class="sxs-lookup"><span data-stu-id="387f2-104">SYNOPSIS</span></span>
<span data-ttu-id="387f2-105">停用本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="387f2-105">Disables a local user account.</span></span>

## <span data-ttu-id="387f2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="387f2-106">SYNTAX</span></span>

### <span data-ttu-id="387f2-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="387f2-107">InputObject</span></span>

```
Disable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="387f2-108">預設</span><span class="sxs-lookup"><span data-stu-id="387f2-108">Default</span></span>

```
Disable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="387f2-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="387f2-109">SecurityIdentifier</span></span>

```
Disable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="387f2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="387f2-110">DESCRIPTION</span></span>
<span data-ttu-id="387f2-111">**LocalUser** 指令 Cmdlet 會停用本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="387f2-111">The **Disable-LocalUser** cmdlet disables local user accounts.</span></span>
<span data-ttu-id="387f2-112">當使用者帳戶停用時，使用者就無法登入。</span><span class="sxs-lookup"><span data-stu-id="387f2-112">When a user account is disabled, the user cannot log on.</span></span>
<span data-ttu-id="387f2-113">當使用者帳戶啟用時，使用者可以登入。</span><span class="sxs-lookup"><span data-stu-id="387f2-113">When a user account is enabled, the user can log on.</span></span>

> [!NOTE]
> <span data-ttu-id="387f2-114">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="387f2-114">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="387f2-115">範例</span><span class="sxs-lookup"><span data-stu-id="387f2-115">EXAMPLES</span></span>

### <span data-ttu-id="387f2-116">範例1：指定名稱以停用帳戶</span><span class="sxs-lookup"><span data-stu-id="387f2-116">Example 1: Disable an account by specifying a name</span></span>

```
PS C:\> Disable-LocalUser -Name "Admin02"
```

<span data-ttu-id="387f2-117">此命令會停用名為 Admin02 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="387f2-117">This command disables the user account named Admin02.</span></span>

### <span data-ttu-id="387f2-118">範例2：使用管線停用帳戶</span><span class="sxs-lookup"><span data-stu-id="387f2-118">Example 2: Disable an account by using the pipeline</span></span>

```
PS C:\> Get-LocalUser Guest | Disable-LocalUser
```

<span data-ttu-id="387f2-119">此命令會使用 **LocalUser 取得** 內建的來賓帳戶，然後使用管線運算子將它傳遞給目前的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="387f2-119">This command gets the built-in Guest account by using **Get-LocalUser** , and then passes it to the current cmdlet by using the pipeline operator.</span></span>
<span data-ttu-id="387f2-120">該 Cmdlet 會停用該帳戶。</span><span class="sxs-lookup"><span data-stu-id="387f2-120">That cmdlet disables that account.</span></span>

## <span data-ttu-id="387f2-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="387f2-121">PARAMETERS</span></span>

### <span data-ttu-id="387f2-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="387f2-122">-InputObject</span></span>
<span data-ttu-id="387f2-123">指定此 Cmdlet 停用的使用者帳戶陣列。</span><span class="sxs-lookup"><span data-stu-id="387f2-123">Specifies an array of user accounts that this cmdlet disables.</span></span>
<span data-ttu-id="387f2-124">若要取得使用者帳戶，請使用 Get-LocalUser Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="387f2-124">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="387f2-125">-Name</span><span class="sxs-lookup"><span data-stu-id="387f2-125">-Name</span></span>
<span data-ttu-id="387f2-126">指定此 Cmdlet 停用之使用者帳戶名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="387f2-126">Specifies an array of names of the user accounts that this cmdlet disables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="387f2-127">-SID</span><span class="sxs-lookup"><span data-stu-id="387f2-127">-SID</span></span>
<span data-ttu-id="387f2-128">指定此 Cmdlet 停用的使用者帳戶陣列。</span><span class="sxs-lookup"><span data-stu-id="387f2-128">Specifies an array of user accounts that this cmdlet disables.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="387f2-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="387f2-129">-Confirm</span></span>
<span data-ttu-id="387f2-130">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="387f2-130">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="387f2-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="387f2-131">-WhatIf</span></span>
<span data-ttu-id="387f2-132">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="387f2-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="387f2-133">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="387f2-133">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="387f2-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="387f2-134">CommonParameters</span></span>
<span data-ttu-id="387f2-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="387f2-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="387f2-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="387f2-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="387f2-137">輸入</span><span class="sxs-lookup"><span data-stu-id="387f2-137">INPUTS</span></span>

### <span data-ttu-id="387f2-138">SecurityAccountsManager. LocalUser，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="387f2-138">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="387f2-139">您可以使用管線將本機使用者、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="387f2-139">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="387f2-140">輸出</span><span class="sxs-lookup"><span data-stu-id="387f2-140">OUTPUTS</span></span>

### <span data-ttu-id="387f2-141">無</span><span class="sxs-lookup"><span data-stu-id="387f2-141">None</span></span>
<span data-ttu-id="387f2-142">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="387f2-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="387f2-143">注意</span><span class="sxs-lookup"><span data-stu-id="387f2-143">NOTES</span></span>

* <span data-ttu-id="387f2-144">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="387f2-144">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="387f2-145">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="387f2-145">The possible sources are as follows:</span></span>

- <span data-ttu-id="387f2-146">本機</span><span class="sxs-lookup"><span data-stu-id="387f2-146">Local</span></span>
- <span data-ttu-id="387f2-147">Active Directory</span><span class="sxs-lookup"><span data-stu-id="387f2-147">Active Directory</span></span>
- <span data-ttu-id="387f2-148">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="387f2-148">Azure Active Directory group</span></span>
- <span data-ttu-id="387f2-149">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="387f2-149">Microsoft Account</span></span>

<span data-ttu-id="387f2-150">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="387f2-150">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="387f2-151">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="387f2-151">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="387f2-152">相關連結</span><span class="sxs-lookup"><span data-stu-id="387f2-152">RELATED LINKS</span></span>

[<span data-ttu-id="387f2-153">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-153">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="387f2-154">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-154">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="387f2-155">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-155">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="387f2-156">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-156">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="387f2-157">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-157">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="387f2-158">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="387f2-158">Set-LocalUser</span></span>](Set-LocalUser.md)
