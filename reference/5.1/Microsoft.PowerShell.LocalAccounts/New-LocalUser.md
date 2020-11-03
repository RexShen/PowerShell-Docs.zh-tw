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
# New-LocalUser

## 概要

建立本機使用者帳戶。

## SYNTAX

### 密碼 (預設) 

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NoPassword

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`New-LocalUser`Cmdlet 會建立本機使用者帳戶。 此 Cmdlet 會建立本機使用者帳戶或連接到 Microsoft 帳戶的本機使用者帳戶。

> [!NOTE]
> 64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。

## 範例

### 範例1：建立使用者帳戶

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

此命令會建立本機使用者帳戶，且不會指定 **AccountExpires** 或 **Password** 參數。 因此，帳戶預設不會過期或有密碼。

### 範例2：建立具有密碼的使用者帳戶

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

第一個命令會使用 Cmdlet 提示您輸入密碼 `Read-Host` 。 此命令會將密碼儲存為變數中的安全字串 `$Password` 。

第二個命令會使用儲存在中的密碼來建立本機使用者帳戶 `$Password` 。 此命令會指定使用者帳戶的使用者名稱、完整名稱和描述。

## PARAMETERS

### -AccountExpires

指定使用者帳戶到期的時間。 若要取得 **DateTime** 物件，請使用 `Get-Date` Cmdlet。
如果您未指定此參數，帳戶就不會過期。

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

### -AccountNeverExpires

指出帳戶沒有過期。

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

### -Description

指定使用者帳戶的批註。
長度上限為48個字元。

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

### -已停用

指出此 Cmdlet 會將使用者帳戶建立為停用。

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

### -FullName

指定使用者帳戶的完整名稱。 完整名稱與使用者帳戶的使用者名稱不同。

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

### -Name

指定使用者帳戶的使用者名稱。

如果您建立本機系統的本機使用者帳戶，使用者名稱最多可以包含20個大寫字元或小寫字元。 使用者名稱不能包含下列字元：

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

使用者名稱不能只包含句號 `.` 或空格。

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

### -NoPassword

指出使用者帳戶沒有密碼。

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

### -Password

指定使用者帳戶的密碼。 您可以使用 `Read-Host -GetCredential` 、 `Get-Credential` 或 `ConvertTo-SecureString` 來建立密碼的 **SecureString** 物件。

如果您省略 **Password** 和 **NoPassword** 參數， `New-LocalUser` 會提示您輸入新使用者的密碼。

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

### -PasswordNeverExpires

指出密碼是否過期。

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

### -UserMayNotChangePassword

指出使用者無法變更使用者帳戶的密碼。

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

### -Confirm

在執行 Cmdlet 前提示您確認。

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

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.string、System.string、System.string、System.object、SecureString

您可以使用管線將字串、 **DateTime** 物件、布林值或安全字串傳送至此 Cmdlet。

## 輸出

### SecurityAccountsManager. LocalUser。

此 Cmdlet 會傳回 **LocalUser** 物件。
此物件提供使用者帳戶的相關資訊。

## 注意

- 使用者名稱不能與電腦上的其他任何使用者名稱或組名相同。 使用者名稱不能只包含句號 `.` 或空格。 使用者名稱最多可以包含20個大寫字元或小寫字元。 使用者名稱不能包含下列字元：

`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`

- 密碼最多可包含127個字元。
- **PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。 可能的來源如下所示：

  - 本機
  - Active Directory
  - Azure Active Directory 群組
  - Microsoft 帳戶

> [!NOTE]
> 只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。 針對較舊的版本，屬性為空白。

## 相關連結

[Disable-LocalUser](Disable-LocalUser.md)

[Enable-LocalUser](Enable-LocalUser.md)

[Get-LocalUser](Get-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)

[Set-LocalUser](Set-LocalUser.md)
