---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroup
ms.openlocfilehash: 2cd77c2766840527825b0ccf68abaac3c2ea6c16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202239"
---
# <span data-ttu-id="2f7a8-103">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2f7a8-103">Get-LocalGroup</span></span>

## <span data-ttu-id="2f7a8-104">概要</span><span class="sxs-lookup"><span data-stu-id="2f7a8-104">SYNOPSIS</span></span>
<span data-ttu-id="2f7a8-105">取得本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-105">Gets the local security groups.</span></span>

## <span data-ttu-id="2f7a8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f7a8-106">SYNTAX</span></span>

### <span data-ttu-id="2f7a8-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="2f7a8-107">Default (Default)</span></span>

```
Get-LocalGroup [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2f7a8-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="2f7a8-108">SecurityIdentifier</span></span>

```
Get-LocalGroup [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="2f7a8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2f7a8-109">DESCRIPTION</span></span>
<span data-ttu-id="2f7a8-110">**LocalGroup 指令程式** 會取得安全性帳戶管理員中的本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-110">The **Get-LocalGroup** cmdlet gets local security groups in Security Account Manager.</span></span>
<span data-ttu-id="2f7a8-111">此 Cmdlet 會取得您建立的預設內建組和本機安全性群組。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-111">This cmdlet gets default built-in groups and local security groups that you create.</span></span>

> [!NOTE]
> <span data-ttu-id="2f7a8-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="2f7a8-113">範例</span><span class="sxs-lookup"><span data-stu-id="2f7a8-113">EXAMPLES</span></span>

### <span data-ttu-id="2f7a8-114">範例1：取得系統管理員群組</span><span class="sxs-lookup"><span data-stu-id="2f7a8-114">Example 1: Get the Administrators group</span></span>

```
PS C:\> Get-LocalGroup -Name "Administrators"
Name           Description
----           -----------
Administrators Administrators have complete and unrestricted access to the computer/domain
```

<span data-ttu-id="2f7a8-115">此命令會取得本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-115">This command gets the local Administrators group.</span></span>
<span data-ttu-id="2f7a8-116">此命令會在主控台中顯示群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-116">The command displays properties of the group in the console.</span></span>

## <span data-ttu-id="2f7a8-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f7a8-117">PARAMETERS</span></span>

### <span data-ttu-id="2f7a8-118">-Name</span><span class="sxs-lookup"><span data-stu-id="2f7a8-118">-Name</span></span>
<span data-ttu-id="2f7a8-119">指定此 Cmdlet 取得之安全性群組的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-119">Specifies an array of names of security groups that this cmdlet gets.</span></span>
<span data-ttu-id="2f7a8-120">您可以使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-120">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2f7a8-121">-SID</span><span class="sxs-lookup"><span data-stu-id="2f7a8-121">-SID</span></span>
<span data-ttu-id="2f7a8-122">指定此 Cmdlet 所取得安全性群組 (Sid) 的安全識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-122">Specifies an array of security IDs (SIDs) of security groups that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2f7a8-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f7a8-123">CommonParameters</span></span>
<span data-ttu-id="2f7a8-124">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f7a8-125">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f7a8-126">輸入</span><span class="sxs-lookup"><span data-stu-id="2f7a8-126">INPUTS</span></span>

### <span data-ttu-id="2f7a8-127">System.string、SecurityIdentifier、system.object</span><span class="sxs-lookup"><span data-stu-id="2f7a8-127">System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="2f7a8-128">您可以使用管線將字串或 SID 傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-128">You can pipe a string or a SID to this cmdlet.</span></span>

## <span data-ttu-id="2f7a8-129">輸出</span><span class="sxs-lookup"><span data-stu-id="2f7a8-129">OUTPUTS</span></span>

### <span data-ttu-id="2f7a8-130">SecurityAccountsManager. LocalGroup。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-130">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="2f7a8-131">此 Cmdlet 會傳回本機群組。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-131">This cmdlet returns a local group.</span></span>

## <span data-ttu-id="2f7a8-132">注意</span><span class="sxs-lookup"><span data-stu-id="2f7a8-132">NOTES</span></span>

* <span data-ttu-id="2f7a8-133">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-133">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="2f7a8-134">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="2f7a8-134">The possible sources are as follows:</span></span>

- <span data-ttu-id="2f7a8-135">本機</span><span class="sxs-lookup"><span data-stu-id="2f7a8-135">Local</span></span>
- <span data-ttu-id="2f7a8-136">Active Directory</span><span class="sxs-lookup"><span data-stu-id="2f7a8-136">Active Directory</span></span>
- <span data-ttu-id="2f7a8-137">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="2f7a8-137">Azure Active Directory group</span></span>
- <span data-ttu-id="2f7a8-138">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="2f7a8-138">Microsoft Account</span></span>

<span data-ttu-id="2f7a8-139">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-139">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="2f7a8-140">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="2f7a8-140">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="2f7a8-141">相關連結</span><span class="sxs-lookup"><span data-stu-id="2f7a8-141">RELATED LINKS</span></span>

[<span data-ttu-id="2f7a8-142">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2f7a8-142">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="2f7a8-143">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2f7a8-143">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="2f7a8-144">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2f7a8-144">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="2f7a8-145">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="2f7a8-145">Set-LocalGroup</span></span>](Set-LocalGroup.md)
