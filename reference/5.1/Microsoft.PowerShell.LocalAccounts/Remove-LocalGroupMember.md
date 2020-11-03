---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203627"
---
# <span data-ttu-id="f85ba-103">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="f85ba-103">Remove-LocalGroupMember</span></span>

## <span data-ttu-id="f85ba-104">概要</span><span class="sxs-lookup"><span data-stu-id="f85ba-104">SYNOPSIS</span></span>
<span data-ttu-id="f85ba-105">從本機群組移除成員。</span><span class="sxs-lookup"><span data-stu-id="f85ba-105">Removes members from a local group.</span></span>

## <span data-ttu-id="f85ba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f85ba-106">SYNTAX</span></span>

### <span data-ttu-id="f85ba-107">Group</span><span class="sxs-lookup"><span data-stu-id="f85ba-107">Group</span></span>

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f85ba-108">預設</span><span class="sxs-lookup"><span data-stu-id="f85ba-108">Default</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f85ba-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f85ba-109">SecurityIdentifier</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f85ba-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f85ba-110">DESCRIPTION</span></span>
<span data-ttu-id="f85ba-111">**LocalGroupMember** 指令 Cmdlet 會從本機群組中移除使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="f85ba-111">The **Remove-LocalGroupMember** cmdlet removes users or groups from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="f85ba-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="f85ba-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="f85ba-113">範例</span><span class="sxs-lookup"><span data-stu-id="f85ba-113">EXAMPLES</span></span>

### <span data-ttu-id="f85ba-114">範例1：從 Administrators 群組移除成員</span><span class="sxs-lookup"><span data-stu-id="f85ba-114">Example 1: Remove members from the Administrators group</span></span>

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

<span data-ttu-id="f85ba-115">此命令會從本機系統管理員群組中移除數個成員。</span><span class="sxs-lookup"><span data-stu-id="f85ba-115">This command removes several members from the local Administrators group.</span></span>
<span data-ttu-id="f85ba-116">此 Cmdlet 移除的成員包括本機使用者帳戶、Microsoft 帳戶、Azure Active Directory 帳戶和網域群組。</span><span class="sxs-lookup"><span data-stu-id="f85ba-116">The members that this cmdlet removes include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span>
<span data-ttu-id="f85ba-117">此範例會在 Outlook.com 中使用帳戶的使用者名稱預留位置值。</span><span class="sxs-lookup"><span data-stu-id="f85ba-117">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

## <span data-ttu-id="f85ba-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f85ba-118">PARAMETERS</span></span>

### <span data-ttu-id="f85ba-119">-Group</span><span class="sxs-lookup"><span data-stu-id="f85ba-119">-Group</span></span>
<span data-ttu-id="f85ba-120">指定此 Cmdlet 從中移除成員的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="f85ba-120">Specifies the security group from which this cmdlet removes members.</span></span>

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

### <span data-ttu-id="f85ba-121">-成員</span><span class="sxs-lookup"><span data-stu-id="f85ba-121">-Member</span></span>
<span data-ttu-id="f85ba-122">指定此 Cmdlet 從安全性群組移除的使用者或群組陣列。</span><span class="sxs-lookup"><span data-stu-id="f85ba-122">Specifies an array of users or groups that this cmdlet removes from a security group.</span></span>
<span data-ttu-id="f85ba-123">您可以依名稱、安全識別碼 (SID) 或 **LocalPrincipal** 物件來指定使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="f85ba-123">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>
<span data-ttu-id="f85ba-124">指定 S-R-I-s-S 中的 SID 字串。</span><span class="sxs-lookup"><span data-stu-id="f85ba-124">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="f85ba-125">.</span><span class="sxs-lookup"><span data-stu-id="f85ba-125">.</span></span> <span data-ttu-id="f85ba-126">.</span><span class="sxs-lookup"><span data-stu-id="f85ba-126">.</span></span>
<span data-ttu-id="f85ba-127">format。</span><span class="sxs-lookup"><span data-stu-id="f85ba-127">format.</span></span>

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

### <span data-ttu-id="f85ba-128">-Name</span><span class="sxs-lookup"><span data-stu-id="f85ba-128">-Name</span></span>
<span data-ttu-id="f85ba-129">指定此 Cmdlet 從中移除成員的安全性群組名稱。</span><span class="sxs-lookup"><span data-stu-id="f85ba-129">Specifies the name of the security group from which this cmdlet removes members.</span></span>

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

### <span data-ttu-id="f85ba-130">-SID</span><span class="sxs-lookup"><span data-stu-id="f85ba-130">-SID</span></span>
<span data-ttu-id="f85ba-131">指定此 Cmdlet 從中移除成員之安全性群組的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="f85ba-131">Specifies the security ID of the security group from which this cmdlet removes members.</span></span>

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

### <span data-ttu-id="f85ba-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f85ba-132">-Confirm</span></span>
<span data-ttu-id="f85ba-133">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f85ba-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f85ba-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f85ba-134">-WhatIf</span></span>
<span data-ttu-id="f85ba-135">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f85ba-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f85ba-136">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f85ba-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f85ba-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f85ba-137">CommonParameters</span></span>
<span data-ttu-id="f85ba-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f85ba-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f85ba-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f85ba-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f85ba-140">輸入</span><span class="sxs-lookup"><span data-stu-id="f85ba-140">INPUTS</span></span>

### <span data-ttu-id="f85ba-141">SecurityAccountsManager. LocalPrincipal，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="f85ba-141">System.Management.Automation.SecurityAccountsManager.LocalPrincipal, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="f85ba-142">您可以使用管線將本機主體、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f85ba-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="f85ba-143">輸出</span><span class="sxs-lookup"><span data-stu-id="f85ba-143">OUTPUTS</span></span>

### <span data-ttu-id="f85ba-144">無</span><span class="sxs-lookup"><span data-stu-id="f85ba-144">None</span></span>
<span data-ttu-id="f85ba-145">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f85ba-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f85ba-146">注意</span><span class="sxs-lookup"><span data-stu-id="f85ba-146">NOTES</span></span>

* <span data-ttu-id="f85ba-147">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="f85ba-147">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="f85ba-148">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="f85ba-148">The possible sources are as follows:</span></span>

- <span data-ttu-id="f85ba-149">本機</span><span class="sxs-lookup"><span data-stu-id="f85ba-149">Local</span></span>
- <span data-ttu-id="f85ba-150">Active Directory</span><span class="sxs-lookup"><span data-stu-id="f85ba-150">Active Directory</span></span>
- <span data-ttu-id="f85ba-151">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="f85ba-151">Azure Active Directory group</span></span>
- <span data-ttu-id="f85ba-152">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="f85ba-152">Microsoft Account</span></span>

<span data-ttu-id="f85ba-153">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="f85ba-153">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="f85ba-154">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="f85ba-154">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="f85ba-155">相關連結</span><span class="sxs-lookup"><span data-stu-id="f85ba-155">RELATED LINKS</span></span>

[<span data-ttu-id="f85ba-156">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="f85ba-156">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="f85ba-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="f85ba-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="f85ba-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="f85ba-158">New-LocalGroup</span></span>](New-LocalGroup.md)
