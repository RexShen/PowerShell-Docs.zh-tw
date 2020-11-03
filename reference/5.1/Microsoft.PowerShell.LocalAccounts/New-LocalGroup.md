---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalGroup
ms.openlocfilehash: de66ad724d3cfee2d296d3b431618768a9cd38da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203631"
---
# <span data-ttu-id="2d304-103">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2d304-103">New-LocalGroup</span></span>

## <span data-ttu-id="2d304-104">概要</span><span class="sxs-lookup"><span data-stu-id="2d304-104">SYNOPSIS</span></span>
<span data-ttu-id="2d304-105">建立本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="2d304-105">Creates a local security group.</span></span>

## <span data-ttu-id="2d304-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2d304-106">SYNTAX</span></span>

```
New-LocalGroup [-Description <String>] [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2d304-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2d304-107">DESCRIPTION</span></span>
<span data-ttu-id="2d304-108">**LocalGroup 指令程式** 會在安全性帳戶管理員中建立本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="2d304-108">The **New-LocalGroup** cmdlet creates a local security group in the Security Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="2d304-109">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="2d304-109">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="2d304-110">範例</span><span class="sxs-lookup"><span data-stu-id="2d304-110">EXAMPLES</span></span>

### <span data-ttu-id="2d304-111">範例1：建立安全性群組</span><span class="sxs-lookup"><span data-stu-id="2d304-111">Example 1: Create a security group</span></span>

```
PS C:\> New-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="2d304-112">此命令會建立名為 SecurityGroup04 的群組。</span><span class="sxs-lookup"><span data-stu-id="2d304-112">This command creates a group named SecurityGroup04.</span></span>

## <span data-ttu-id="2d304-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d304-113">PARAMETERS</span></span>

### <span data-ttu-id="2d304-114">-Description</span><span class="sxs-lookup"><span data-stu-id="2d304-114">-Description</span></span>
<span data-ttu-id="2d304-115">指定群組的批註。</span><span class="sxs-lookup"><span data-stu-id="2d304-115">Specifies a comment for the group.</span></span>
<span data-ttu-id="2d304-116">長度上限為48個字元。</span><span class="sxs-lookup"><span data-stu-id="2d304-116">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2d304-117">-Name</span><span class="sxs-lookup"><span data-stu-id="2d304-117">-Name</span></span>
<span data-ttu-id="2d304-118">指定群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="2d304-118">Specifies a name for the group.</span></span>
<span data-ttu-id="2d304-119">最大長度是 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="2d304-119">The maximum length is 256 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2d304-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2d304-120">-Confirm</span></span>
<span data-ttu-id="2d304-121">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2d304-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2d304-122">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2d304-122">-WhatIf</span></span>
<span data-ttu-id="2d304-123">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2d304-123">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2d304-124">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2d304-124">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2d304-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d304-125">CommonParameters</span></span>
<span data-ttu-id="2d304-126">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2d304-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d304-127">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2d304-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d304-128">輸入</span><span class="sxs-lookup"><span data-stu-id="2d304-128">INPUTS</span></span>

### <span data-ttu-id="2d304-129">System.String</span><span class="sxs-lookup"><span data-stu-id="2d304-129">System.String</span></span>
<span data-ttu-id="2d304-130">您可以使用管線傳送字串至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2d304-130">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="2d304-131">輸出</span><span class="sxs-lookup"><span data-stu-id="2d304-131">OUTPUTS</span></span>

### <span data-ttu-id="2d304-132">SecurityAccountsManager. LocalGroup。</span><span class="sxs-lookup"><span data-stu-id="2d304-132">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="2d304-133">此 Cmdlet 會傳回安全性群組。</span><span class="sxs-lookup"><span data-stu-id="2d304-133">This cmdlet returns a security group.</span></span>

## <span data-ttu-id="2d304-134">注意</span><span class="sxs-lookup"><span data-stu-id="2d304-134">NOTES</span></span>

* <span data-ttu-id="2d304-135">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="2d304-135">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="2d304-136">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="2d304-136">The possible sources are as follows:</span></span>

- <span data-ttu-id="2d304-137">本機</span><span class="sxs-lookup"><span data-stu-id="2d304-137">Local</span></span>
- <span data-ttu-id="2d304-138">Active Directory</span><span class="sxs-lookup"><span data-stu-id="2d304-138">Active Directory</span></span>
- <span data-ttu-id="2d304-139">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="2d304-139">Azure Active Directory group</span></span>
- <span data-ttu-id="2d304-140">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="2d304-140">Microsoft Account</span></span>

<span data-ttu-id="2d304-141">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="2d304-141">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="2d304-142">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="2d304-142">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="2d304-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="2d304-143">RELATED LINKS</span></span>

[<span data-ttu-id="2d304-144">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2d304-144">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="2d304-145">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2d304-145">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="2d304-146">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2d304-146">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="2d304-147">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2d304-147">Set-LocalGroup</span></span>](Set-LocalGroup.md)
