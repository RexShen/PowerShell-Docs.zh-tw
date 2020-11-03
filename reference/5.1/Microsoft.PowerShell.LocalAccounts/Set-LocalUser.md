---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204095"
---
# <span data-ttu-id="5b3b4-103">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-103">Set-LocalUser</span></span>

## <span data-ttu-id="5b3b4-104">概要</span><span class="sxs-lookup"><span data-stu-id="5b3b4-104">SYNOPSIS</span></span>
<span data-ttu-id="5b3b4-105">修改本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-105">Modifies a local user account.</span></span>

## <span data-ttu-id="5b3b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b3b4-106">SYNTAX</span></span>

### <span data-ttu-id="5b3b4-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="5b3b4-107">Name (Default)</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5b3b4-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="5b3b4-108">InputObject</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5b3b4-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="5b3b4-109">SecurityIdentifier</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5b3b4-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3b4-110">DESCRIPTION</span></span>
<span data-ttu-id="5b3b4-111">**LocalUser** 指令 Cmdlet 會修改本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-111">The **Set-LocalUser** cmdlet modifies a local user account.</span></span>
<span data-ttu-id="5b3b4-112">此 Cmdlet 可以重設本機使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-112">This cmdlet can reset the password of a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="5b3b4-113">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-113">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="5b3b4-114">範例</span><span class="sxs-lookup"><span data-stu-id="5b3b4-114">EXAMPLES</span></span>

### <span data-ttu-id="5b3b4-115">範例1：變更使用者帳戶的描述</span><span class="sxs-lookup"><span data-stu-id="5b3b4-115">Example 1: Change a description of a user account</span></span>

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

<span data-ttu-id="5b3b4-116">此命令會變更名為 Admin07 的使用者帳戶的描述。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-116">This command changes the description of a user account named Admin07.</span></span>

### <span data-ttu-id="5b3b4-117">範例2：變更帳戶的密碼</span><span class="sxs-lookup"><span data-stu-id="5b3b4-117">Example 2: Change the password on an account</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

<span data-ttu-id="5b3b4-118">第一個命令會使用 Read-Host Cmdlet 提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-118">The first command prompts you for a password by using the Read-Host cmdlet.</span></span>
<span data-ttu-id="5b3b4-119">此命令會將密碼儲存為 $Password 變數中的安全字串。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-119">The command stores the password as a secure string in the $Password variable.</span></span>

<span data-ttu-id="5b3b4-120">第二個命令會取得名為 User02 的使用者帳戶，方法是使用 **LocalUser** 。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-120">The second command gets a user account named User02 by using **Get-LocalUser** .</span></span>
<span data-ttu-id="5b3b4-121">此命令會將帳戶儲存在 $UserAccount 變數中。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-121">The command stores the account in the $UserAccount variable.</span></span>

<span data-ttu-id="5b3b4-122">第三個命令會在 $UserAccount 中儲存的使用者帳戶上設定新密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-122">The third command sets the new password on the user account stored in $UserAccount.</span></span>

## <span data-ttu-id="5b3b4-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5b3b4-123">PARAMETERS</span></span>

### <span data-ttu-id="5b3b4-124">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="5b3b4-124">-AccountExpires</span></span>
<span data-ttu-id="5b3b4-125">指定使用者帳戶到期的時間。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-125">Specifies when the user account expires.</span></span>
<span data-ttu-id="5b3b4-126">若要取得 **DateTime** 物件，請使用 Get-Date Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-126">To obtain a **DateTime** object, use the Get-Date cmdlet.</span></span>

<span data-ttu-id="5b3b4-127">如果您不想讓帳戶到期，請指定 *AccountNeverExpires* 參數。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-127">If you do not want the account to expire, specify the *AccountNeverExpires* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-128">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="5b3b4-128">-AccountNeverExpires</span></span>
<span data-ttu-id="5b3b4-129">指出帳戶沒有過期。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-129">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-130">-Description</span><span class="sxs-lookup"><span data-stu-id="5b3b4-130">-Description</span></span>
<span data-ttu-id="5b3b4-131">指定使用者帳戶的批註。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-131">Specifies a comment for the user account.</span></span>
<span data-ttu-id="5b3b4-132">長度上限為48個字元。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-132">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-133">-FullName</span><span class="sxs-lookup"><span data-stu-id="5b3b4-133">-FullName</span></span>
<span data-ttu-id="5b3b4-134">指定使用者帳戶的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-134">Specifies the full name for the user account.</span></span>
<span data-ttu-id="5b3b4-135">完整名稱與使用者帳戶的使用者名稱不同。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-135">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5b3b4-136">-InputObject</span></span>
<span data-ttu-id="5b3b4-137">指定此 Cmdlet 變更的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-137">Specifies the user account that this cmdlet changes.</span></span>
<span data-ttu-id="5b3b4-138">若要取得使用者帳戶，請使用 Get-LocalUser Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-138">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="5b3b4-139">-Name</span><span class="sxs-lookup"><span data-stu-id="5b3b4-139">-Name</span></span>
<span data-ttu-id="5b3b4-140">指定此 Cmdlet 所變更之使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-140">Specifies the name of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-141">-Password</span><span class="sxs-lookup"><span data-stu-id="5b3b4-141">-Password</span></span>
<span data-ttu-id="5b3b4-142">指定使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-142">Specifies a password for the user account.</span></span>
<span data-ttu-id="5b3b4-143">如果使用者帳戶連接到 Microsoft 帳戶，請不要設定密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-143">If the user account is connected to a Microsoft account, do not set a password.</span></span>

<span data-ttu-id="5b3b4-144">您可以使用 `Read-Host -GetCredential` 、取得認證或 ConvertTo-SecureString 來建立密碼的 **SecureString** 物件。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-144">You can use `Read-Host -GetCredential`, Get-Credential, or ConvertTo-SecureString to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="5b3b4-145">如果您省略 *Password* 和 *NoPassword* 參數， **LocalUser** 會提示您輸入使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-145">If you omit the *Password* and *NoPassword* parameters, **Set-LocalUser** prompts you for the user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-146">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="5b3b4-146">-PasswordNeverExpires</span></span>
<span data-ttu-id="5b3b4-147">指出密碼是否過期。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-147">Indicates whether the password expires.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-148">-SID</span><span class="sxs-lookup"><span data-stu-id="5b3b4-148">-SID</span></span>
<span data-ttu-id="5b3b4-149">指定此 Cmdlet 所變更之使用者帳戶 (SID) 的安全識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-149">Specifies the security ID (SID) of the user account that this cmdlet changes.</span></span>

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

### <span data-ttu-id="5b3b4-150">-UserMayChangePassword</span><span class="sxs-lookup"><span data-stu-id="5b3b4-150">-UserMayChangePassword</span></span>
<span data-ttu-id="5b3b4-151">指出使用者可以變更使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-151">Indicates that the user can change the password on the user account.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5b3b4-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5b3b4-152">-Confirm</span></span>
<span data-ttu-id="5b3b4-153">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5b3b4-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5b3b4-154">-WhatIf</span></span>
<span data-ttu-id="5b3b4-155">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5b3b4-156">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5b3b4-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b3b4-157">CommonParameters</span></span>
<span data-ttu-id="5b3b4-158">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b3b4-159">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b3b4-160">輸入</span><span class="sxs-lookup"><span data-stu-id="5b3b4-160">INPUTS</span></span>

### <span data-ttu-id="5b3b4-161">SecurityAccountsManager. LocalUser，System.string，SecurityIdentifier....。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-161">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="5b3b4-162">您可以使用管線將本機使用者、字串或 SID 傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-162">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="5b3b4-163">輸出</span><span class="sxs-lookup"><span data-stu-id="5b3b4-163">OUTPUTS</span></span>

### <span data-ttu-id="5b3b4-164">無</span><span class="sxs-lookup"><span data-stu-id="5b3b4-164">None</span></span>
<span data-ttu-id="5b3b4-165">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-165">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5b3b4-166">注意</span><span class="sxs-lookup"><span data-stu-id="5b3b4-166">NOTES</span></span>

* <span data-ttu-id="5b3b4-167">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-167">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="5b3b4-168">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="5b3b4-168">The possible sources are as follows:</span></span>

- <span data-ttu-id="5b3b4-169">本機</span><span class="sxs-lookup"><span data-stu-id="5b3b4-169">Local</span></span>
- <span data-ttu-id="5b3b4-170">Active Directory</span><span class="sxs-lookup"><span data-stu-id="5b3b4-170">Active Directory</span></span>
- <span data-ttu-id="5b3b4-171">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="5b3b4-171">Azure Active Directory group</span></span>
- <span data-ttu-id="5b3b4-172">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="5b3b4-172">Microsoft Account</span></span>

<span data-ttu-id="5b3b4-173">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-173">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="5b3b4-174">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="5b3b4-174">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="5b3b4-175">相關連結</span><span class="sxs-lookup"><span data-stu-id="5b3b4-175">RELATED LINKS</span></span>

[<span data-ttu-id="5b3b4-176">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-176">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="5b3b4-177">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-177">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="5b3b4-178">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-178">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="5b3b4-179">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-179">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="5b3b4-180">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-180">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="5b3b4-181">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="5b3b4-181">Rename-LocalUser</span></span>](Rename-LocalUser.md)
