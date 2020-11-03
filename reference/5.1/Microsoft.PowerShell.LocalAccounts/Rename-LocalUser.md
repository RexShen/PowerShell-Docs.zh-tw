---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalUser
ms.openlocfilehash: fc5740e52e08ad2146981799a4e1659cd420b321
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204103"
---
# <span data-ttu-id="3653e-103">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-103">Rename-LocalUser</span></span>

## <span data-ttu-id="3653e-104">概要</span><span class="sxs-lookup"><span data-stu-id="3653e-104">SYNOPSIS</span></span>
<span data-ttu-id="3653e-105">重新命名本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3653e-105">Renames a local user account.</span></span>

## <span data-ttu-id="3653e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3653e-106">SYNTAX</span></span>

### <span data-ttu-id="3653e-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="3653e-107">InputObject</span></span>

```
Rename-LocalUser [-InputObject] <LocalUser> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3653e-108">預設</span><span class="sxs-lookup"><span data-stu-id="3653e-108">Default</span></span>

```
Rename-LocalUser [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3653e-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3653e-109">SecurityIdentifier</span></span>

```
Rename-LocalUser [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3653e-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3653e-110">DESCRIPTION</span></span>
<span data-ttu-id="3653e-111">LocalUser 指令 Cmdlet 會 **重新** 命名本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3653e-111">The **Rename-LocalUser** cmdlet renames a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="3653e-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="3653e-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="3653e-113">範例</span><span class="sxs-lookup"><span data-stu-id="3653e-113">EXAMPLES</span></span>

### <span data-ttu-id="3653e-114">範例1：重新命名使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="3653e-114">Example 1: Rename a user account</span></span>

```
PS C:\> Rename-LocalUser -Name "Admin02" -NewName "AdminContoso02"
```

<span data-ttu-id="3653e-115">此命令會重新命名名為 Admin02 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3653e-115">This command renames the user account named Admin02.</span></span>

## <span data-ttu-id="3653e-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3653e-116">PARAMETERS</span></span>

### <span data-ttu-id="3653e-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3653e-117">-InputObject</span></span>
<span data-ttu-id="3653e-118">指定此 Cmdlet 重新命名的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3653e-118">Specifies the user account that this cmdlet renames.</span></span>
<span data-ttu-id="3653e-119">若要取得使用者帳戶，請使用 Get-LocalUser Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3653e-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3653e-120">-Name</span><span class="sxs-lookup"><span data-stu-id="3653e-120">-Name</span></span>
<span data-ttu-id="3653e-121">指定此 Cmdlet 重新命名的使用者帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="3653e-121">Specifies the name of the user account that this cmdlet renames.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3653e-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="3653e-122">-NewName</span></span>
<span data-ttu-id="3653e-123">指定使用者帳戶的新名稱。</span><span class="sxs-lookup"><span data-stu-id="3653e-123">Specifies a new name for the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3653e-124">-SID</span><span class="sxs-lookup"><span data-stu-id="3653e-124">-SID</span></span>
<span data-ttu-id="3653e-125">指定此 Cmdlet 重新命名的使用者帳戶 (SID) 的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="3653e-125">Specifies the security ID (SID) of a user accounts that this cmdlet renames.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3653e-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3653e-126">-Confirm</span></span>
<span data-ttu-id="3653e-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3653e-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3653e-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3653e-128">-WhatIf</span></span>
<span data-ttu-id="3653e-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3653e-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3653e-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="3653e-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3653e-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3653e-131">CommonParameters</span></span>
<span data-ttu-id="3653e-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3653e-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3653e-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3653e-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3653e-134">輸入</span><span class="sxs-lookup"><span data-stu-id="3653e-134">INPUTS</span></span>

### <span data-ttu-id="3653e-135">SecurityAccountsManager. LocalUser，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="3653e-135">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="3653e-136">您可以使用管線將本機使用者、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3653e-136">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="3653e-137">輸出</span><span class="sxs-lookup"><span data-stu-id="3653e-137">OUTPUTS</span></span>

### <span data-ttu-id="3653e-138">無</span><span class="sxs-lookup"><span data-stu-id="3653e-138">None</span></span>
<span data-ttu-id="3653e-139">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="3653e-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3653e-140">注意</span><span class="sxs-lookup"><span data-stu-id="3653e-140">NOTES</span></span>

* <span data-ttu-id="3653e-141">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="3653e-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="3653e-142">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="3653e-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="3653e-143">本機</span><span class="sxs-lookup"><span data-stu-id="3653e-143">Local</span></span>
- <span data-ttu-id="3653e-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="3653e-144">Active Directory</span></span>
- <span data-ttu-id="3653e-145">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="3653e-145">Azure Active Directory group</span></span>
- <span data-ttu-id="3653e-146">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="3653e-146">Microsoft Account</span></span>

<span data-ttu-id="3653e-147">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="3653e-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="3653e-148">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="3653e-148">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="3653e-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="3653e-149">RELATED LINKS</span></span>

[<span data-ttu-id="3653e-150">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-150">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="3653e-151">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-151">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="3653e-152">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-152">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="3653e-153">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-153">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="3653e-154">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-154">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="3653e-155">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="3653e-155">Set-LocalUser</span></span>](Set-LocalUser.md)
