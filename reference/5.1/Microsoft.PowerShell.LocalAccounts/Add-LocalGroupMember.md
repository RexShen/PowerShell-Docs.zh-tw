---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202251"
---
# <span data-ttu-id="aead9-103">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="aead9-103">Add-LocalGroupMember</span></span>

## <span data-ttu-id="aead9-104">概要</span><span class="sxs-lookup"><span data-stu-id="aead9-104">SYNOPSIS</span></span>
<span data-ttu-id="aead9-105">將成員新增至本機群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-105">Adds members to a local group.</span></span>

## <span data-ttu-id="aead9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aead9-106">SYNTAX</span></span>

### <span data-ttu-id="aead9-107">Group</span><span class="sxs-lookup"><span data-stu-id="aead9-107">Group</span></span>

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="aead9-108">預設</span><span class="sxs-lookup"><span data-stu-id="aead9-108">Default</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aead9-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="aead9-109">SecurityIdentifier</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="aead9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="aead9-110">DESCRIPTION</span></span>

<span data-ttu-id="aead9-111">此 `Add-LocalGroupMember` Cmdlet 會將使用者或群組新增至本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-111">The `Add-LocalGroupMember` cmdlet adds users or groups to a local security group.</span></span> <span data-ttu-id="aead9-112">指派給群組的所有權利及權限都會指派給該群組中的所有成員。</span><span class="sxs-lookup"><span data-stu-id="aead9-112">All the rights and permissions that are assigned to a group are assigned to all members of that group.</span></span>

<span data-ttu-id="aead9-113">在本機電腦上的 Administrators 群組成員擁有該電腦的 [完全控制] 權限。</span><span class="sxs-lookup"><span data-stu-id="aead9-113">Members of the Administrators group on a local computer have Full Control permissions on that computer.</span></span> <span data-ttu-id="aead9-114">限制 Administrators 群組中的使用者數目。</span><span class="sxs-lookup"><span data-stu-id="aead9-114">Limit the number of users in the Administrators group.</span></span>

<span data-ttu-id="aead9-115">如果將電腦加入網域中，則您可以將使用者帳戶、電腦帳戶及群組帳戶從該網域及受信任的網域新增到本機群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-115">If the computer is joined to a domain, you can add user accounts, computer accounts, and group accounts from that domain and from trusted domains to a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="aead9-116">如果電腦已加入網域，而您嘗試新增的本機使用者與網域成員具有相同的名稱，則會新增網域成員。</span><span class="sxs-lookup"><span data-stu-id="aead9-116">If the computer is joined to a domain and you try to add a local user that has the same name as a member of the domain it adds the domain member.</span></span>

## <span data-ttu-id="aead9-117">範例</span><span class="sxs-lookup"><span data-stu-id="aead9-117">EXAMPLES</span></span>

### <span data-ttu-id="aead9-118">範例1：將成員新增至系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="aead9-118">Example 1: Add members to the Administrators group</span></span>

<span data-ttu-id="aead9-119">此命令會將數個成員新增至本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-119">This command adds several members to the local Administrators group.</span></span> <span data-ttu-id="aead9-120">新成員包含本機使用者帳戶、Microsoft 帳戶、Azure Active Directory 帳戶和網域群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-120">The new members include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span> <span data-ttu-id="aead9-121">此範例會在 Outlook.com 中使用帳戶的使用者名稱預留位置值。</span><span class="sxs-lookup"><span data-stu-id="aead9-121">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## <span data-ttu-id="aead9-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aead9-122">PARAMETERS</span></span>

### <span data-ttu-id="aead9-123">-Group</span><span class="sxs-lookup"><span data-stu-id="aead9-123">-Group</span></span>

<span data-ttu-id="aead9-124">指定此 Cmdlet 新增成員的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-124">Specifies the security group to which this cmdlet adds members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aead9-125">-成員</span><span class="sxs-lookup"><span data-stu-id="aead9-125">-Member</span></span>

<span data-ttu-id="aead9-126">指定此 Cmdlet 新增至安全性群組的使用者或群組陣列。</span><span class="sxs-lookup"><span data-stu-id="aead9-126">Specifies an array of users or groups that this cmdlet adds to a security group.</span></span> <span data-ttu-id="aead9-127">您可以依名稱、安全識別碼 (SID) 或 **LocalPrincipal** 物件來指定使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="aead9-127">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aead9-128">-Name</span><span class="sxs-lookup"><span data-stu-id="aead9-128">-Name</span></span>

<span data-ttu-id="aead9-129">指定此 Cmdlet 新增成員的安全性群組名稱。</span><span class="sxs-lookup"><span data-stu-id="aead9-129">Specifies the name of the security group to which this cmdlet adds members.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aead9-130">-SID</span><span class="sxs-lookup"><span data-stu-id="aead9-130">-SID</span></span>

<span data-ttu-id="aead9-131">指定此 Cmdlet 新增成員之安全性群組的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="aead9-131">Specifies the security ID of the security group to which this cmdlet adds members.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aead9-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aead9-132">-Confirm</span></span>

<span data-ttu-id="aead9-133">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="aead9-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aead9-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aead9-134">-WhatIf</span></span>

<span data-ttu-id="aead9-135">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="aead9-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="aead9-136">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="aead9-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="aead9-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aead9-137">CommonParameters</span></span>

<span data-ttu-id="aead9-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="aead9-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aead9-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="aead9-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aead9-140">輸入</span><span class="sxs-lookup"><span data-stu-id="aead9-140">INPUTS</span></span>

### <span data-ttu-id="aead9-141">SecurityAccountsManager. LocalGroup，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="aead9-141">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="aead9-142">您可以使用管線將本機主體、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aead9-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="aead9-143">輸出</span><span class="sxs-lookup"><span data-stu-id="aead9-143">OUTPUTS</span></span>

### <span data-ttu-id="aead9-144">無</span><span class="sxs-lookup"><span data-stu-id="aead9-144">None</span></span>

<span data-ttu-id="aead9-145">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="aead9-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aead9-146">注意</span><span class="sxs-lookup"><span data-stu-id="aead9-146">NOTES</span></span>

<span data-ttu-id="aead9-147">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="aead9-147">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

<span data-ttu-id="aead9-148">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="aead9-148">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="aead9-149">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="aead9-149">The possible sources are as follows:</span></span>

- <span data-ttu-id="aead9-150">本機</span><span class="sxs-lookup"><span data-stu-id="aead9-150">Local</span></span>
- <span data-ttu-id="aead9-151">Active Directory</span><span class="sxs-lookup"><span data-stu-id="aead9-151">Active Directory</span></span>
- <span data-ttu-id="aead9-152">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="aead9-152">Azure Active Directory group</span></span>
- <span data-ttu-id="aead9-153">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="aead9-153">Microsoft Account</span></span>

<span data-ttu-id="aead9-154">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="aead9-154">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="aead9-155">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="aead9-155">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="aead9-156">相關連結</span><span class="sxs-lookup"><span data-stu-id="aead9-156">RELATED LINKS</span></span>

[<span data-ttu-id="aead9-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="aead9-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="aead9-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="aead9-158">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="aead9-159">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="aead9-159">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
