---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203624"
---
# <span data-ttu-id="45633-103">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="45633-103">Remove-LocalGroup</span></span>

## <span data-ttu-id="45633-104">概要</span><span class="sxs-lookup"><span data-stu-id="45633-104">SYNOPSIS</span></span>
<span data-ttu-id="45633-105">刪除本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="45633-105">Deletes local security groups.</span></span>

## <span data-ttu-id="45633-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45633-106">SYNTAX</span></span>

### <span data-ttu-id="45633-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="45633-107">InputObject</span></span>

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="45633-108">預設</span><span class="sxs-lookup"><span data-stu-id="45633-108">Default</span></span>

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="45633-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="45633-109">SecurityIdentifier</span></span>

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="45633-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="45633-110">DESCRIPTION</span></span>
<span data-ttu-id="45633-111">**LocalGroup** 指令 Cmdlet 會刪除本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="45633-111">The **Remove-LocalGroup** cmdlet deletes local security groups.</span></span>
<span data-ttu-id="45633-112">此 Cmdlet 只會刪除本機群組。</span><span class="sxs-lookup"><span data-stu-id="45633-112">This cmdlet deletes only a local group.</span></span>
<span data-ttu-id="45633-113">它不會刪除屬於該群組的使用者帳戶、電腦帳戶或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="45633-113">It does not delete the user accounts, computer accounts, or group accounts that belong to that group.</span></span>
<span data-ttu-id="45633-114">您無法復原已刪除的群組。</span><span class="sxs-lookup"><span data-stu-id="45633-114">You cannot recover a deleted group.</span></span>

<span data-ttu-id="45633-115">如果您刪除群組，然後再建立另一個具有相同組名的群組，則必須為新群組設定新的許可權。</span><span class="sxs-lookup"><span data-stu-id="45633-115">If you delete a group and then create another group that has the same group name, you must set new permissions for the new group.</span></span>
<span data-ttu-id="45633-116">新群組不會繼承指派給該群組的許可權。</span><span class="sxs-lookup"><span data-stu-id="45633-116">The new group does not inherit the permissions that were assigned to the group.</span></span>

> [!NOTE]
> <span data-ttu-id="45633-117">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="45633-117">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="45633-118">範例</span><span class="sxs-lookup"><span data-stu-id="45633-118">EXAMPLES</span></span>

### <span data-ttu-id="45633-119">範例1：刪除安全性群組</span><span class="sxs-lookup"><span data-stu-id="45633-119">Example 1: Delete a security group</span></span>

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="45633-120">此命令會刪除名為 SecurityGroup04 的群組。</span><span class="sxs-lookup"><span data-stu-id="45633-120">This command deletes the group named SecurityGroup04.</span></span>

## <span data-ttu-id="45633-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="45633-121">PARAMETERS</span></span>

### <span data-ttu-id="45633-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="45633-122">-InputObject</span></span>
<span data-ttu-id="45633-123">指定此 Cmdlet 刪除的安全性群組陣列。</span><span class="sxs-lookup"><span data-stu-id="45633-123">Specifies an array of security groups that this cmdlet deletes.</span></span>
<span data-ttu-id="45633-124">若要取得群組，請使用 Get-LocalGroup Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45633-124">To obtain groups, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45633-125">-Name</span><span class="sxs-lookup"><span data-stu-id="45633-125">-Name</span></span>
<span data-ttu-id="45633-126">指定此 Cmdlet 所刪除之安全性群組的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="45633-126">Specifies an array of names of the security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="45633-127">-SID</span><span class="sxs-lookup"><span data-stu-id="45633-127">-SID</span></span>
<span data-ttu-id="45633-128">指定此 Cmdlet 所刪除之安全性群組 (Sid) 的安全識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="45633-128">Specifies an array of security IDs (SIDs) of security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="45633-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="45633-129">-Confirm</span></span>
<span data-ttu-id="45633-130">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="45633-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="45633-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="45633-131">-WhatIf</span></span>
<span data-ttu-id="45633-132">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="45633-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="45633-133">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="45633-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="45633-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45633-134">CommonParameters</span></span>
<span data-ttu-id="45633-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="45633-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45633-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="45633-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45633-137">輸入</span><span class="sxs-lookup"><span data-stu-id="45633-137">INPUTS</span></span>

### <span data-ttu-id="45633-138">SecurityAccountsManager. LocalGroup，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="45633-138">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="45633-139">您可以使用管線將安全性群組、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="45633-139">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="45633-140">輸出</span><span class="sxs-lookup"><span data-stu-id="45633-140">OUTPUTS</span></span>

### <span data-ttu-id="45633-141">無</span><span class="sxs-lookup"><span data-stu-id="45633-141">None</span></span>
<span data-ttu-id="45633-142">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="45633-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="45633-143">注意</span><span class="sxs-lookup"><span data-stu-id="45633-143">NOTES</span></span>

* <span data-ttu-id="45633-144">此 Cmdlet 無法刪除下列預設群組：</span><span class="sxs-lookup"><span data-stu-id="45633-144">This cmdlet cannot delete the following default groups:</span></span>

- <span data-ttu-id="45633-145">系統管理員</span><span class="sxs-lookup"><span data-stu-id="45633-145">Administrators</span></span>
- <span data-ttu-id="45633-146">Backup Operators</span><span class="sxs-lookup"><span data-stu-id="45633-146">Backup Operators</span></span>
- <span data-ttu-id="45633-147">Cryptographic Operators</span><span class="sxs-lookup"><span data-stu-id="45633-147">Cryptographic Operators</span></span>
- <span data-ttu-id="45633-148">Distributed COM Users</span><span class="sxs-lookup"><span data-stu-id="45633-148">Distributed COM Users</span></span>
- <span data-ttu-id="45633-149">Event Log Readers</span><span class="sxs-lookup"><span data-stu-id="45633-149">Event Log Readers</span></span>
- <span data-ttu-id="45633-150">Guests</span><span class="sxs-lookup"><span data-stu-id="45633-150">Guests</span></span>
- <span data-ttu-id="45633-151">Hyper-V 系統管理員</span><span class="sxs-lookup"><span data-stu-id="45633-151">Hyper-V Administrators</span></span>
- <span data-ttu-id="45633-152">IIS_IUSRS</span><span class="sxs-lookup"><span data-stu-id="45633-152">IIS_IUSRS</span></span>
- <span data-ttu-id="45633-153">Network Configuration Operators</span><span class="sxs-lookup"><span data-stu-id="45633-153">Network Configuration Operators</span></span>
- <span data-ttu-id="45633-154">效能記錄使用者</span><span class="sxs-lookup"><span data-stu-id="45633-154">Performance Log Users</span></span>
- <span data-ttu-id="45633-155">效能監視器使用者</span><span class="sxs-lookup"><span data-stu-id="45633-155">Performance Monitor Users</span></span>
- <span data-ttu-id="45633-156">Power Users</span><span class="sxs-lookup"><span data-stu-id="45633-156">Power Users</span></span>
- <span data-ttu-id="45633-157">Remote Desktop Users</span><span class="sxs-lookup"><span data-stu-id="45633-157">Remote Desktop Users</span></span>
- <span data-ttu-id="45633-158">遠端管理使用者</span><span class="sxs-lookup"><span data-stu-id="45633-158">Remote Management Users</span></span>
- <span data-ttu-id="45633-159">Replicator</span><span class="sxs-lookup"><span data-stu-id="45633-159">Replicator</span></span>
- <span data-ttu-id="45633-160">使用者</span><span class="sxs-lookup"><span data-stu-id="45633-160">Users</span></span>
- <span data-ttu-id="45633-161">WinRMRemoteWMIUsers__</span><span class="sxs-lookup"><span data-stu-id="45633-161">WinRMRemoteWMIUsers__</span></span>

* <span data-ttu-id="45633-162">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="45633-162">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="45633-163">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="45633-163">The possible sources are as follows:</span></span>

- <span data-ttu-id="45633-164">本機</span><span class="sxs-lookup"><span data-stu-id="45633-164">Local</span></span>
- <span data-ttu-id="45633-165">Active Directory</span><span class="sxs-lookup"><span data-stu-id="45633-165">Active Directory</span></span>
- <span data-ttu-id="45633-166">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="45633-166">Azure Active Directory group</span></span>
- <span data-ttu-id="45633-167">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="45633-167">Microsoft Account</span></span>

<span data-ttu-id="45633-168">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="45633-168">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="45633-169">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="45633-169">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="45633-170">相關連結</span><span class="sxs-lookup"><span data-stu-id="45633-170">RELATED LINKS</span></span>

[<span data-ttu-id="45633-171">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="45633-171">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="45633-172">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="45633-172">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="45633-173">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="45633-173">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="45633-174">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="45633-174">Set-LocalGroup</span></span>](Set-LocalGroup.md)
