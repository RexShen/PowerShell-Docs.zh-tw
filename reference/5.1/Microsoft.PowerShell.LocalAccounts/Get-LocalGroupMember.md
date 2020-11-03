---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202232"
---
# <span data-ttu-id="4217d-103">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="4217d-103">Get-LocalGroupMember</span></span>

## <span data-ttu-id="4217d-104">概要</span><span class="sxs-lookup"><span data-stu-id="4217d-104">SYNOPSIS</span></span>
<span data-ttu-id="4217d-105">取得本機群組的成員。</span><span class="sxs-lookup"><span data-stu-id="4217d-105">Gets members from a local group.</span></span>

## <span data-ttu-id="4217d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4217d-106">SYNTAX</span></span>

### <span data-ttu-id="4217d-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="4217d-107">Default (Default)</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### <span data-ttu-id="4217d-108">Group</span><span class="sxs-lookup"><span data-stu-id="4217d-108">Group</span></span>

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### <span data-ttu-id="4217d-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="4217d-109">SecurityIdentifier</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## <span data-ttu-id="4217d-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4217d-110">DESCRIPTION</span></span>
<span data-ttu-id="4217d-111">**LocalGroupMember** 指令 Cmdlet 會從本機群組取得成員。</span><span class="sxs-lookup"><span data-stu-id="4217d-111">The **Get-LocalGroupMember** cmdlet gets members from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="4217d-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="4217d-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="4217d-113">範例</span><span class="sxs-lookup"><span data-stu-id="4217d-113">EXAMPLES</span></span>

### <span data-ttu-id="4217d-114">範例1：取得系統管理員群組的所有成員</span><span class="sxs-lookup"><span data-stu-id="4217d-114">Example 1: Get all members of the Administrators group</span></span>

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

<span data-ttu-id="4217d-115">此命令會取得本機系統管理員群組的所有成員。</span><span class="sxs-lookup"><span data-stu-id="4217d-115">This command gets all the members of the local Administrators group.</span></span>

## <span data-ttu-id="4217d-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4217d-116">PARAMETERS</span></span>

### <span data-ttu-id="4217d-117">-Group</span><span class="sxs-lookup"><span data-stu-id="4217d-117">-Group</span></span>
<span data-ttu-id="4217d-118">指定此 Cmdlet 從中取得成員的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="4217d-118">Specifies the security group from which this cmdlet gets members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4217d-119">-成員</span><span class="sxs-lookup"><span data-stu-id="4217d-119">-Member</span></span>
<span data-ttu-id="4217d-120">指定此 Cmdlet 從安全性群組取得的使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="4217d-120">Specifies a user or group that this cmdlet gets from a security group.</span></span>
<span data-ttu-id="4217d-121">您可以依名稱或安全性識別碼指定使用者或群組 (SID) 。</span><span class="sxs-lookup"><span data-stu-id="4217d-121">You can specify users or groups by name or security ID (SID).</span></span>
<span data-ttu-id="4217d-122">指定 S-R-I-s-S 中的 SID 字串。</span><span class="sxs-lookup"><span data-stu-id="4217d-122">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="4217d-123">.</span><span class="sxs-lookup"><span data-stu-id="4217d-123">.</span></span> <span data-ttu-id="4217d-124">.</span><span class="sxs-lookup"><span data-stu-id="4217d-124">.</span></span>
<span data-ttu-id="4217d-125">format。</span><span class="sxs-lookup"><span data-stu-id="4217d-125">format.</span></span>
<span data-ttu-id="4217d-126">您可以使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4217d-126">You can use wildcard characters.</span></span>
<span data-ttu-id="4217d-127">如果您未指定此參數，Cmdlet 會取得群組的所有成員。</span><span class="sxs-lookup"><span data-stu-id="4217d-127">If you do not specify this parameter, the cmdlet gets all members of the group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4217d-128">-Name</span><span class="sxs-lookup"><span data-stu-id="4217d-128">-Name</span></span>
<span data-ttu-id="4217d-129">指定此 Cmdlet 從中取得成員之安全性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="4217d-129">Specifies the name of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="4217d-130">-SID</span><span class="sxs-lookup"><span data-stu-id="4217d-130">-SID</span></span>
<span data-ttu-id="4217d-131">指定此 Cmdlet 從中取得成員之安全性群組的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="4217d-131">Specifies the security ID of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="4217d-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4217d-132">CommonParameters</span></span>
<span data-ttu-id="4217d-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4217d-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4217d-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4217d-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4217d-135">輸入</span><span class="sxs-lookup"><span data-stu-id="4217d-135">INPUTS</span></span>

### <span data-ttu-id="4217d-136">SecurityAccountsManager. LocalGroup，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="4217d-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="4217d-137">您可以使用管線將本機群組、字串或 SID 傳送到此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4217d-137">You can pipe a local group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="4217d-138">輸出</span><span class="sxs-lookup"><span data-stu-id="4217d-138">OUTPUTS</span></span>

### <span data-ttu-id="4217d-139">SecurityAccountsManager. LocalPrincipal</span><span class="sxs-lookup"><span data-stu-id="4217d-139">Microsoft.SecurityAccountsManager.LocalPrincipal</span></span>
<span data-ttu-id="4217d-140">此 Cmdlet 會傳回本機主體。</span><span class="sxs-lookup"><span data-stu-id="4217d-140">This cmdlet returns local principals.</span></span>

## <span data-ttu-id="4217d-141">注意</span><span class="sxs-lookup"><span data-stu-id="4217d-141">NOTES</span></span>

* <span data-ttu-id="4217d-142">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="4217d-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="4217d-143">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="4217d-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="4217d-144">本機</span><span class="sxs-lookup"><span data-stu-id="4217d-144">Local</span></span>
- <span data-ttu-id="4217d-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="4217d-145">Active Directory</span></span>
- <span data-ttu-id="4217d-146">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="4217d-146">Azure Active Directory group</span></span>
- <span data-ttu-id="4217d-147">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="4217d-147">Microsoft Account</span></span>

<span data-ttu-id="4217d-148">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="4217d-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="4217d-149">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="4217d-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="4217d-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="4217d-150">RELATED LINKS</span></span>

[<span data-ttu-id="4217d-151">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="4217d-151">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="4217d-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="4217d-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="4217d-153">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="4217d-153">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
