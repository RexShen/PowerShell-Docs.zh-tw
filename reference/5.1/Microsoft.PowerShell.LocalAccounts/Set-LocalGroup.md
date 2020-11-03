---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalGroup
ms.openlocfilehash: 471c3c7bc01bf26dfe9d8eec26e4414464cae02e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204100"
---
# <span data-ttu-id="89dbf-103">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="89dbf-103">Set-LocalGroup</span></span>

## <span data-ttu-id="89dbf-104">概要</span><span class="sxs-lookup"><span data-stu-id="89dbf-104">SYNOPSIS</span></span>
<span data-ttu-id="89dbf-105">變更本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="89dbf-105">Changes a local security group.</span></span>

## <span data-ttu-id="89dbf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="89dbf-106">SYNTAX</span></span>

### <span data-ttu-id="89dbf-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="89dbf-107">InputObject</span></span>

```
Set-LocalGroup -Description <String> [-InputObject] <LocalGroup> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="89dbf-108">預設</span><span class="sxs-lookup"><span data-stu-id="89dbf-108">Default</span></span>

```
Set-LocalGroup -Description <String> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="89dbf-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="89dbf-109">SecurityIdentifier</span></span>

```
Set-LocalGroup -Description <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="89dbf-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="89dbf-110">DESCRIPTION</span></span>
<span data-ttu-id="89dbf-111">**LocalGroup** 指令 Cmdlet 會變更本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="89dbf-111">The **Set-LocalGroup** cmdlet changes a local security group.</span></span>

## <span data-ttu-id="89dbf-112">範例</span><span class="sxs-lookup"><span data-stu-id="89dbf-112">EXAMPLES</span></span>

### <span data-ttu-id="89dbf-113">範例1：變更群組描述</span><span class="sxs-lookup"><span data-stu-id="89dbf-113">Example 1: Change a group description</span></span>

```
PS C:\> Set-LocalGroup -Name "SecurityGroup04" -Description "This is a sample description."
```

<span data-ttu-id="89dbf-114">此命令會變更本機群組的描述。</span><span class="sxs-lookup"><span data-stu-id="89dbf-114">This command changes the description of a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="89dbf-115">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="89dbf-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="89dbf-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89dbf-116">PARAMETERS</span></span>

### <span data-ttu-id="89dbf-117">-Description</span><span class="sxs-lookup"><span data-stu-id="89dbf-117">-Description</span></span>
<span data-ttu-id="89dbf-118">指定群組的批註。</span><span class="sxs-lookup"><span data-stu-id="89dbf-118">Specifies a comment for the group.</span></span>
<span data-ttu-id="89dbf-119">長度上限為48個字元。</span><span class="sxs-lookup"><span data-stu-id="89dbf-119">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89dbf-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="89dbf-120">-InputObject</span></span>
<span data-ttu-id="89dbf-121">指定此 Cmdlet 所變更的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="89dbf-121">Specifies the security group that this cmdlet changes.</span></span>
<span data-ttu-id="89dbf-122">若要取得安全性群組，請使用 Get-LocalGroup Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89dbf-122">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

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

### <span data-ttu-id="89dbf-123">-Name</span><span class="sxs-lookup"><span data-stu-id="89dbf-123">-Name</span></span>
<span data-ttu-id="89dbf-124">指定此 Cmdlet 所變更之安全性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="89dbf-124">Specifies the name of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="89dbf-125">-SID</span><span class="sxs-lookup"><span data-stu-id="89dbf-125">-SID</span></span>
<span data-ttu-id="89dbf-126">指定此 Cmdlet 所變更安全性群組 (SID) 的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="89dbf-126">Specifies the security ID (SID) of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="89dbf-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="89dbf-127">-Confirm</span></span>
<span data-ttu-id="89dbf-128">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="89dbf-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="89dbf-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="89dbf-129">-WhatIf</span></span>
<span data-ttu-id="89dbf-130">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="89dbf-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="89dbf-131">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="89dbf-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="89dbf-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89dbf-132">CommonParameters</span></span>
<span data-ttu-id="89dbf-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="89dbf-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89dbf-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="89dbf-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89dbf-135">輸入</span><span class="sxs-lookup"><span data-stu-id="89dbf-135">INPUTS</span></span>

### <span data-ttu-id="89dbf-136">SecurityAccountsManager. LocalGroup，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="89dbf-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="89dbf-137">您可以使用管線將安全性群組、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89dbf-137">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="89dbf-138">輸出</span><span class="sxs-lookup"><span data-stu-id="89dbf-138">OUTPUTS</span></span>

### <span data-ttu-id="89dbf-139">無</span><span class="sxs-lookup"><span data-stu-id="89dbf-139">None</span></span>
<span data-ttu-id="89dbf-140">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="89dbf-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="89dbf-141">注意</span><span class="sxs-lookup"><span data-stu-id="89dbf-141">NOTES</span></span>

* <span data-ttu-id="89dbf-142">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="89dbf-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="89dbf-143">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="89dbf-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="89dbf-144">本機</span><span class="sxs-lookup"><span data-stu-id="89dbf-144">Local</span></span>
- <span data-ttu-id="89dbf-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="89dbf-145">Active Directory</span></span>
- <span data-ttu-id="89dbf-146">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="89dbf-146">Azure Active Directory group</span></span>
- <span data-ttu-id="89dbf-147">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="89dbf-147">Microsoft Account</span></span>

<span data-ttu-id="89dbf-148">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="89dbf-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="89dbf-149">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="89dbf-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="89dbf-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="89dbf-150">RELATED LINKS</span></span>

[<span data-ttu-id="89dbf-151">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="89dbf-151">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="89dbf-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="89dbf-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="89dbf-153">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="89dbf-153">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="89dbf-154">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="89dbf-154">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)
