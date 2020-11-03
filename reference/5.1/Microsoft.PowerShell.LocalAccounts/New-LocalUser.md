---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203623"
---
# <span data-ttu-id="54094-103">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-103">New-LocalUser</span></span>

## <span data-ttu-id="54094-104">概要</span><span class="sxs-lookup"><span data-stu-id="54094-104">SYNOPSIS</span></span>

<span data-ttu-id="54094-105">建立本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="54094-105">Creates a local user account.</span></span>

## <span data-ttu-id="54094-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="54094-106">SYNTAX</span></span>

### <span data-ttu-id="54094-107">密碼 (預設) </span><span class="sxs-lookup"><span data-stu-id="54094-107">Password (Default)</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="54094-108">NoPassword</span><span class="sxs-lookup"><span data-stu-id="54094-108">NoPassword</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="54094-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="54094-109">DESCRIPTION</span></span>

<span data-ttu-id="54094-110">`New-LocalUser`Cmdlet 會建立本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="54094-110">The `New-LocalUser` cmdlet creates a local user account.</span></span> <span data-ttu-id="54094-111">此 Cmdlet 會建立本機使用者帳戶或連接到 Microsoft 帳戶的本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="54094-111">This cmdlet creates a local user account or a local user account that is connected to a Microsoft account.</span></span>

> [!NOTE]
> <span data-ttu-id="54094-112">64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。</span><span class="sxs-lookup"><span data-stu-id="54094-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="54094-113">範例</span><span class="sxs-lookup"><span data-stu-id="54094-113">EXAMPLES</span></span>

### <span data-ttu-id="54094-114">範例1：建立使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="54094-114">Example 1: Create a user account</span></span>

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

<span data-ttu-id="54094-115">此命令會建立本機使用者帳戶，且不會指定 **AccountExpires** 或 **Password** 參數。</span><span class="sxs-lookup"><span data-stu-id="54094-115">This command creates a local user account and does not specify the **AccountExpires** or **Password** parameters.</span></span> <span data-ttu-id="54094-116">因此，帳戶預設不會過期或有密碼。</span><span class="sxs-lookup"><span data-stu-id="54094-116">Therefore, the account doesn't expire or have a password by default.</span></span>

### <span data-ttu-id="54094-117">範例2：建立具有密碼的使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="54094-117">Example 2: Create a user account that has a password</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

<span data-ttu-id="54094-118">第一個命令會使用 Cmdlet 提示您輸入密碼 `Read-Host` 。</span><span class="sxs-lookup"><span data-stu-id="54094-118">The first command prompts you for a password by using the `Read-Host` cmdlet.</span></span> <span data-ttu-id="54094-119">此命令會將密碼儲存為變數中的安全字串 `$Password` 。</span><span class="sxs-lookup"><span data-stu-id="54094-119">The command stores the password as a secure string in the `$Password` variable.</span></span>

<span data-ttu-id="54094-120">第二個命令會使用儲存在中的密碼來建立本機使用者帳戶 `$Password` 。</span><span class="sxs-lookup"><span data-stu-id="54094-120">The second command creates a local user account by using the password stored in `$Password`.</span></span> <span data-ttu-id="54094-121">此命令會指定使用者帳戶的使用者名稱、完整名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="54094-121">The command specifies a user name, full name, and description for the user account.</span></span>

## <span data-ttu-id="54094-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54094-122">PARAMETERS</span></span>

### <span data-ttu-id="54094-123">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="54094-123">-AccountExpires</span></span>

<span data-ttu-id="54094-124">指定使用者帳戶到期的時間。</span><span class="sxs-lookup"><span data-stu-id="54094-124">Specifies when the user account expires.</span></span> <span data-ttu-id="54094-125">若要取得 **DateTime** 物件，請使用 `Get-Date` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="54094-125">To obtain a **DateTime** object, use the `Get-Date` cmdlet.</span></span>
<span data-ttu-id="54094-126">如果您未指定此參數，帳戶就不會過期。</span><span class="sxs-lookup"><span data-stu-id="54094-126">If you do not specify this parameter, the account does not expire.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-127">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="54094-127">-AccountNeverExpires</span></span>

<span data-ttu-id="54094-128">指出帳戶沒有過期。</span><span class="sxs-lookup"><span data-stu-id="54094-128">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-129">-Description</span><span class="sxs-lookup"><span data-stu-id="54094-129">-Description</span></span>

<span data-ttu-id="54094-130">指定使用者帳戶的批註。</span><span class="sxs-lookup"><span data-stu-id="54094-130">Specifies a comment for the user account.</span></span>
<span data-ttu-id="54094-131">長度上限為48個字元。</span><span class="sxs-lookup"><span data-stu-id="54094-131">The maximum length is 48 characters.</span></span>

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

### <span data-ttu-id="54094-132">-已停用</span><span class="sxs-lookup"><span data-stu-id="54094-132">-Disabled</span></span>

<span data-ttu-id="54094-133">指出此 Cmdlet 會將使用者帳戶建立為停用。</span><span class="sxs-lookup"><span data-stu-id="54094-133">Indicates that this cmdlet creates the user account as disabled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-134">-FullName</span><span class="sxs-lookup"><span data-stu-id="54094-134">-FullName</span></span>

<span data-ttu-id="54094-135">指定使用者帳戶的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="54094-135">Specifies the full name for the user account.</span></span> <span data-ttu-id="54094-136">完整名稱與使用者帳戶的使用者名稱不同。</span><span class="sxs-lookup"><span data-stu-id="54094-136">The full name differs from the user name of the user account.</span></span>

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

### <span data-ttu-id="54094-137">-Name</span><span class="sxs-lookup"><span data-stu-id="54094-137">-Name</span></span>

<span data-ttu-id="54094-138">指定使用者帳戶的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="54094-138">Specifies the user name for the user account.</span></span>

<span data-ttu-id="54094-139">如果您建立本機系統的本機使用者帳戶，使用者名稱最多可以包含20個大寫字元或小寫字元。</span><span class="sxs-lookup"><span data-stu-id="54094-139">If you create a local user account for the local system, the user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="54094-140">使用者名稱不能包含下列字元：</span><span class="sxs-lookup"><span data-stu-id="54094-140">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="54094-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="54094-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

<span data-ttu-id="54094-142">使用者名稱不能只包含句號 `.` 或空格。</span><span class="sxs-lookup"><span data-stu-id="54094-142">A user name cannot consist only of periods `.` or spaces.</span></span>

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

### <span data-ttu-id="54094-143">-NoPassword</span><span class="sxs-lookup"><span data-stu-id="54094-143">-NoPassword</span></span>

<span data-ttu-id="54094-144">指出使用者帳戶沒有密碼。</span><span class="sxs-lookup"><span data-stu-id="54094-144">Indicates that the user account does not have a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-145">-Password</span><span class="sxs-lookup"><span data-stu-id="54094-145">-Password</span></span>

<span data-ttu-id="54094-146">指定使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="54094-146">Specifies a password for the user account.</span></span> <span data-ttu-id="54094-147">您可以使用 `Read-Host -GetCredential` 、 `Get-Credential` 或 `ConvertTo-SecureString` 來建立密碼的 **SecureString** 物件。</span><span class="sxs-lookup"><span data-stu-id="54094-147">You can use `Read-Host -GetCredential`, `Get-Credential`, or `ConvertTo-SecureString` to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="54094-148">如果您省略 **Password** 和 **NoPassword** 參數， `New-LocalUser` 會提示您輸入新使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="54094-148">If you omit the **Password** and **NoPassword** parameters, `New-LocalUser` prompts you for the new user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-149">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="54094-149">-PasswordNeverExpires</span></span>

<span data-ttu-id="54094-150">指出密碼是否過期。</span><span class="sxs-lookup"><span data-stu-id="54094-150">Indicates whether the password expires.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-151">-UserMayNotChangePassword</span><span class="sxs-lookup"><span data-stu-id="54094-151">-UserMayNotChangePassword</span></span>

<span data-ttu-id="54094-152">指出使用者無法變更使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="54094-152">Indicates that the user cannot change the password on the user account.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="54094-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="54094-153">-Confirm</span></span>

<span data-ttu-id="54094-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="54094-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="54094-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="54094-155">-WhatIf</span></span>

<span data-ttu-id="54094-156">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="54094-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="54094-157">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="54094-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="54094-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54094-158">CommonParameters</span></span>

<span data-ttu-id="54094-159">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="54094-159">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="54094-160">如需詳細資訊，請參閱 [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="54094-160">For more information, see [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="54094-161">輸入</span><span class="sxs-lookup"><span data-stu-id="54094-161">INPUTS</span></span>

### <span data-ttu-id="54094-162">System.string、System.string、System.string、System.object、SecureString</span><span class="sxs-lookup"><span data-stu-id="54094-162">System.String, System.DateTime, System.Boolean, System.Security.SecureString</span></span>

<span data-ttu-id="54094-163">您可以使用管線將字串、 **DateTime** 物件、布林值或安全字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="54094-163">You can pipe a string, a **DateTime** object, a boolean value, or a secure string to this cmdlet.</span></span>

## <span data-ttu-id="54094-164">輸出</span><span class="sxs-lookup"><span data-stu-id="54094-164">OUTPUTS</span></span>

### <span data-ttu-id="54094-165">SecurityAccountsManager. LocalUser。</span><span class="sxs-lookup"><span data-stu-id="54094-165">System.Management.Automation.SecurityAccountsManager.LocalUser</span></span>

<span data-ttu-id="54094-166">此 Cmdlet 會傳回 **LocalUser** 物件。</span><span class="sxs-lookup"><span data-stu-id="54094-166">This cmdlet returns a **LocalUser** object.</span></span>
<span data-ttu-id="54094-167">此物件提供使用者帳戶的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="54094-167">This object provides information about the user account.</span></span>

## <span data-ttu-id="54094-168">注意</span><span class="sxs-lookup"><span data-stu-id="54094-168">NOTES</span></span>

- <span data-ttu-id="54094-169">使用者名稱不能與電腦上的其他任何使用者名稱或組名相同。</span><span class="sxs-lookup"><span data-stu-id="54094-169">A user name cannot be identical to any other user name or group name on the computer.</span></span> <span data-ttu-id="54094-170">使用者名稱不能只包含句號 `.` 或空格。</span><span class="sxs-lookup"><span data-stu-id="54094-170">A user name cannot consist only of periods `.` or spaces.</span></span> <span data-ttu-id="54094-171">使用者名稱最多可以包含20個大寫字元或小寫字元。</span><span class="sxs-lookup"><span data-stu-id="54094-171">A user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="54094-172">使用者名稱不能包含下列字元：</span><span class="sxs-lookup"><span data-stu-id="54094-172">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="54094-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="54094-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

- <span data-ttu-id="54094-174">密碼最多可包含127個字元。</span><span class="sxs-lookup"><span data-stu-id="54094-174">A password can contain up to 127 characters.</span></span>
- <span data-ttu-id="54094-175">**PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。</span><span class="sxs-lookup"><span data-stu-id="54094-175">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="54094-176">可能的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="54094-176">The possible sources are as follows:</span></span>

  - <span data-ttu-id="54094-177">本機</span><span class="sxs-lookup"><span data-stu-id="54094-177">Local</span></span>
  - <span data-ttu-id="54094-178">Active Directory</span><span class="sxs-lookup"><span data-stu-id="54094-178">Active Directory</span></span>
  - <span data-ttu-id="54094-179">Azure Active Directory 群組</span><span class="sxs-lookup"><span data-stu-id="54094-179">Azure Active Directory group</span></span>
  - <span data-ttu-id="54094-180">Microsoft 帳戶</span><span class="sxs-lookup"><span data-stu-id="54094-180">Microsoft Account</span></span>

> [!NOTE]
> <span data-ttu-id="54094-181">只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。</span><span class="sxs-lookup"><span data-stu-id="54094-181">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="54094-182">針對較舊的版本，屬性為空白。</span><span class="sxs-lookup"><span data-stu-id="54094-182">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="54094-183">相關連結</span><span class="sxs-lookup"><span data-stu-id="54094-183">RELATED LINKS</span></span>

[<span data-ttu-id="54094-184">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-184">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="54094-185">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-185">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="54094-186">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-186">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="54094-187">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-187">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="54094-188">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-188">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="54094-189">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="54094-189">Set-LocalUser</span></span>](Set-LocalUser.md)
