---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204099"
---
# <span data-ttu-id="24ad3-103">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="24ad3-103">Rename-LocalGroup</span></span>

## <span data-ttu-id="24ad3-104">概要</span><span class="sxs-lookup"><span data-stu-id="24ad3-104">SYNOPSIS</span></span>
<span data-ttu-id="24ad3-105">重新命名本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="24ad3-105">Renames a local security group.</span></span>

## <span data-ttu-id="24ad3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="24ad3-106">SYNTAX</span></span>

### <span data-ttu-id="24ad3-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="24ad3-107">InputObject</span></span>

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="24ad3-108">預設</span><span class="sxs-lookup"><span data-stu-id="24ad3-108">Default</span></span>

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="24ad3-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="24ad3-109">SecurityIdentifier</span></span>

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="24ad3-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="24ad3-110">DESCRIPTION</span></span>
<span data-ttu-id="24ad3-111">LocalGroup 指令 Cmdlet 會 **重新** 命名本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="24ad3-111">The **Rename-LocalGroup** cmdlet renames a local security group.</span></span>

> [!NOTE]
> <span data-ttu-id="24ad3-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="24ad3-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="24ad3-113">範例</span><span class="sxs-lookup"><span data-stu-id="24ad3-113">EXAMPLES</span></span>

### <span data-ttu-id="24ad3-114">範例1：變更群組的名稱</span><span class="sxs-lookup"><span data-stu-id="24ad3-114">Example 1: Change the name of a group</span></span>

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

<span data-ttu-id="24ad3-115">此命令會重新命名名為 SecurityGroup 的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="24ad3-115">This command renames a security group named SecurityGroup.</span></span>

## <span data-ttu-id="24ad3-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="24ad3-116">PARAMETERS</span></span>

### <span data-ttu-id="24ad3-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="24ad3-117">-InputObject</span></span>
<span data-ttu-id="24ad3-118">指定此 Cmdlet 重新命名的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="24ad3-118">Specifies the security group that this cmdlet renames.</span></span>
<span data-ttu-id="24ad3-119">若要取得安全性群組，請使用 Get-LocalGroup Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="24ad3-119">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="24ad3-120">-Name</span><span class="sxs-lookup"><span data-stu-id="24ad3-120">-Name</span></span>
<span data-ttu-id="24ad3-121">指定此 Cmdlet 重新命名之安全性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="24ad3-121">Specifies the name of the security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="24ad3-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="24ad3-122">-NewName</span></span>
<span data-ttu-id="24ad3-123">指定安全性群組的新名稱。</span><span class="sxs-lookup"><span data-stu-id="24ad3-123">Specifies a new name for the security group.</span></span>

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

### <span data-ttu-id="24ad3-124">-SID</span><span class="sxs-lookup"><span data-stu-id="24ad3-124">-SID</span></span>
<span data-ttu-id="24ad3-125">指定此 Cmdlet 重新命名之安全性群組 (SID) 的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="24ad3-125">Specifies the security ID (SID) of a security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="24ad3-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="24ad3-126">-Confirm</span></span>
<span data-ttu-id="24ad3-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="24ad3-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="24ad3-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="24ad3-128">-WhatIf</span></span>
<span data-ttu-id="24ad3-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="24ad3-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="24ad3-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="24ad3-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="24ad3-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24ad3-131">CommonParameters</span></span>
<span data-ttu-id="24ad3-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="24ad3-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24ad3-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="24ad3-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24ad3-134">輸入</span><span class="sxs-lookup"><span data-stu-id="24ad3-134">INPUTS</span></span>

### <span data-ttu-id="24ad3-135">SecurityAccountsManager. LocalGroup，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="24ad3-135">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="24ad3-136">您可以使用管線將安全性群組、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="24ad3-136">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="24ad3-137">輸出</span><span class="sxs-lookup"><span data-stu-id="24ad3-137">OUTPUTS</span></span>

### <span data-ttu-id="24ad3-138">無</span><span class="sxs-lookup"><span data-stu-id="24ad3-138">None</span></span>
<span data-ttu-id="24ad3-139">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="24ad3-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="24ad3-140">注意</span><span class="sxs-lookup"><span data-stu-id="24ad3-140">NOTES</span></span>

* <span data-ttu-id="24ad3-141">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="24ad3-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="24ad3-142">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="24ad3-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="24ad3-143">本機</span><span class="sxs-lookup"><span data-stu-id="24ad3-143">Local</span></span>
- <span data-ttu-id="24ad3-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="24ad3-144">Active Directory</span></span>
- <span data-ttu-id="24ad3-145">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="24ad3-145">Azure Active Directory group</span></span>
- <span data-ttu-id="24ad3-146">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="24ad3-146">Microsoft Account</span></span>

<span data-ttu-id="24ad3-147">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="24ad3-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="24ad3-148">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="24ad3-148">For earlier  versions, the property is blank.</span></span>

## <span data-ttu-id="24ad3-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="24ad3-149">RELATED LINKS</span></span>

[<span data-ttu-id="24ad3-150">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="24ad3-150">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="24ad3-151">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="24ad3-151">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="24ad3-152">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="24ad3-152">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="24ad3-153">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="24ad3-153">Set-LocalGroup</span></span>](Set-LocalGroup.md)
