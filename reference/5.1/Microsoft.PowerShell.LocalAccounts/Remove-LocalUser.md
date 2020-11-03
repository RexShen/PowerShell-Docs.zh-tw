---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalUser
ms.openlocfilehash: de1054971dab19f8cfae654208488ca9ce5e17e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204104"
---
# <span data-ttu-id="2a266-103">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-103">Remove-LocalUser</span></span>

## <span data-ttu-id="2a266-104">概要</span><span class="sxs-lookup"><span data-stu-id="2a266-104">SYNOPSIS</span></span>
<span data-ttu-id="2a266-105">刪除本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a266-105">Deletes local user accounts.</span></span>

## <span data-ttu-id="2a266-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2a266-106">SYNTAX</span></span>

### <span data-ttu-id="2a266-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="2a266-107">InputObject</span></span>

```
Remove-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2a266-108">預設</span><span class="sxs-lookup"><span data-stu-id="2a266-108">Default</span></span>

```
Remove-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2a266-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="2a266-109">SecurityIdentifier</span></span>

```
Remove-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2a266-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2a266-110">DESCRIPTION</span></span>
<span data-ttu-id="2a266-111">**LocalUser** 指令 Cmdlet 會刪除本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a266-111">The **Remove-LocalUser** cmdlet deletes local user accounts.</span></span>

## <span data-ttu-id="2a266-112">範例</span><span class="sxs-lookup"><span data-stu-id="2a266-112">EXAMPLES</span></span>

### <span data-ttu-id="2a266-113">範例1：刪除使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="2a266-113">Example 1: Delete a user account</span></span>

```
PS C:\> Remove-LocalUser -Name "AdminContoso02"
```

<span data-ttu-id="2a266-114">此命令會刪除名為 AdminContoso02 的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a266-114">This command deletes the user account named AdminContoso02.</span></span>

> [!NOTE]
> <span data-ttu-id="2a266-115">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="2a266-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="2a266-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a266-116">PARAMETERS</span></span>

### <span data-ttu-id="2a266-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2a266-117">-InputObject</span></span>
<span data-ttu-id="2a266-118">指定此 Cmdlet 刪除的使用者帳戶陣列。</span><span class="sxs-lookup"><span data-stu-id="2a266-118">Specifies an array of user accounts that this cmdlet deletes.</span></span>
<span data-ttu-id="2a266-119">若要取得使用者帳戶，請使用 Get-LocalUser Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a266-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="2a266-120">-Name</span><span class="sxs-lookup"><span data-stu-id="2a266-120">-Name</span></span>
<span data-ttu-id="2a266-121">指定此 Cmdlet 所刪除之使用者帳戶名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="2a266-121">Specifies an array of names of the user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="2a266-122">-SID</span><span class="sxs-lookup"><span data-stu-id="2a266-122">-SID</span></span>
<span data-ttu-id="2a266-123">指定此 Cmdlet 所刪除之使用者帳戶 (Sid) 的安全識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="2a266-123">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="2a266-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2a266-124">-Confirm</span></span>
<span data-ttu-id="2a266-125">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2a266-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2a266-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2a266-126">-WhatIf</span></span>
<span data-ttu-id="2a266-127">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2a266-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2a266-128">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2a266-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2a266-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a266-129">CommonParameters</span></span>
<span data-ttu-id="2a266-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2a266-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a266-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2a266-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a266-132">輸入</span><span class="sxs-lookup"><span data-stu-id="2a266-132">INPUTS</span></span>

### <span data-ttu-id="2a266-133">SecurityAccountsManager. LocalUser，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="2a266-133">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="2a266-134">您可以使用管線將本機使用者、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a266-134">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="2a266-135">輸出</span><span class="sxs-lookup"><span data-stu-id="2a266-135">OUTPUTS</span></span>

### <span data-ttu-id="2a266-136">無</span><span class="sxs-lookup"><span data-stu-id="2a266-136">None</span></span>
<span data-ttu-id="2a266-137">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2a266-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2a266-138">注意</span><span class="sxs-lookup"><span data-stu-id="2a266-138">NOTES</span></span>

* <span data-ttu-id="2a266-139">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="2a266-139">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="2a266-140">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a266-140">The possible sources are as follows:</span></span>

- <span data-ttu-id="2a266-141">本機</span><span class="sxs-lookup"><span data-stu-id="2a266-141">Local</span></span>
- <span data-ttu-id="2a266-142">Active Directory</span><span class="sxs-lookup"><span data-stu-id="2a266-142">Active Directory</span></span>
- <span data-ttu-id="2a266-143">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="2a266-143">Azure Active Directory group</span></span>
- <span data-ttu-id="2a266-144">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="2a266-144">Microsoft Account</span></span>

<span data-ttu-id="2a266-145">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="2a266-145">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="2a266-146">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="2a266-146">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="2a266-147">相關連結</span><span class="sxs-lookup"><span data-stu-id="2a266-147">RELATED LINKS</span></span>

[<span data-ttu-id="2a266-148">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-148">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="2a266-149">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-149">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="2a266-150">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-150">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="2a266-151">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-151">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="2a266-152">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-152">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="2a266-153">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="2a266-153">Set-LocalUser</span></span>](Set-LocalUser.md)
