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
# Set-LocalUser

## 概要
修改本機使用者帳戶。

## SYNTAX

### Name (預設值)

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**LocalUser** 指令 Cmdlet 會修改本機使用者帳戶。
此 Cmdlet 可以重設本機使用者帳戶的密碼。

> [!NOTE]
> 64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。

## 範例

### 範例1：變更使用者帳戶的描述

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

此命令會變更名為 Admin07 的使用者帳戶的描述。

### 範例2：變更帳戶的密碼

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

第一個命令會使用 Read-Host Cmdlet 提示您輸入密碼。
此命令會將密碼儲存為 $Password 變數中的安全字串。

第二個命令會取得名為 User02 的使用者帳戶，方法是使用 **LocalUser** 。
此命令會將帳戶儲存在 $UserAccount 變數中。

第三個命令會在 $UserAccount 中儲存的使用者帳戶上設定新密碼。

## PARAMETERS

### -AccountExpires
指定使用者帳戶到期的時間。
若要取得 **DateTime** 物件，請使用 Get-Date Cmdlet。

如果您不想讓帳戶到期，請指定 *AccountNeverExpires* 參數。

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

### -AccountNeverExpires
指出帳戶沒有過期。

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
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullName
指定使用者帳戶的完整名稱。
完整名稱與使用者帳戶的使用者名稱不同。

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

### -InputObject
指定此 Cmdlet 變更的使用者帳戶。
若要取得使用者帳戶，請使用 Get-LocalUser Cmdlet。

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

### -Name
指定此 Cmdlet 所變更之使用者帳戶的名稱。

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

### -Password
指定使用者帳戶的密碼。
如果使用者帳戶連接到 Microsoft 帳戶，請不要設定密碼。

您可以使用 `Read-Host -GetCredential` 、取得認證或 ConvertTo-SecureString 來建立密碼的 **SecureString** 物件。

如果您省略 *Password* 和 *NoPassword* 參數， **LocalUser** 會提示您輸入使用者的密碼。

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

### -PasswordNeverExpires
指出密碼是否過期。

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

### -SID
指定此 Cmdlet 所變更之使用者帳戶 (SID) 的安全識別碼。

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

### -UserMayChangePassword
指出使用者可以變更使用者帳戶的密碼。

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
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### SecurityAccountsManager. LocalUser，System.string，SecurityIdentifier....。
您可以使用管線將本機使用者、字串或 SID 傳送給此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* **PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。 可能的來源如下所示：

- 本機
- Active Directory
- Azure Active Directory 群組
- Microsoft 帳戶

只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。 針對較舊的版本，屬性為空白。

## 相關連結

[Disable-LocalUser](Disable-LocalUser.md)

[Enable-LocalUser](Enable-LocalUser.md)

[Get-LocalUser](Get-LocalUser.md)

[New-LocalUser](New-LocalUser.md)

[Remove-LocalUser](Remove-LocalUser.md)

[Rename-LocalUser](Rename-LocalUser.md)
