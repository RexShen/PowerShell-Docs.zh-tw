---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 7ec2c3025f62a64cd24298c0749d40fa5eff4904
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346083"
---
# ConvertFrom-SddlString

## 概要
將 SDDL 字串轉換成自訂物件。

## SYNTAX

### 全部

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## DESCRIPTION

此 `ConvertFrom-SddlString` Cmdlet 會將安全描述項定義語言字串轉換為具有下列屬性的自訂 **PSCustomObject** 物件： Owner、Group、objdescriptor.discretionaryacl、SystemAcl 和 RawDescriptor。

Owner、Group、Objdescriptor.discretionaryacl 和 SystemAcl 屬性包含 SDDL 字串中所指定存取權限的可讀取文字表示。

此 Cmdlet 是在 PowerShell 5.0 中引進。

## 範例

### 範例1：將檔案系統存取權限 SDDL 轉換成 PSCustomObject

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

第一個命令會使用 `Get-Acl` Cmdlet 來取得 C：\Windows 資料夾的安全描述項，並將其儲存在變數中。

第二個命令會使用 `ConvertFrom-SddlString` Cmdlet 來取得 sddl 字串的文字標記法，此物件包含在代表安全描述項之物件的 sddl 屬性中。

### 範例2：將登錄存取權限 SDDL 轉換成 PSCustomObject

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

第一個命令會使用 `Get-Acl` Cmdlet 來取得 HKLM： \ SOFTWARE\Microsoft\ 金鑰的安全描述項，並將其儲存在變數中。

第二個命令會使用 `ConvertFrom-SddlString` Cmdlet 來取得 sddl 字串的文字標記法，此物件包含在代表安全描述項之物件的 sddl 屬性中。

它會使用 `-Type` 參數來指定 SDDL 字串代表登錄安全描述項。

### 範例3：使用 ConvertFrom-SddlString 搭配和不使用參數，將登錄存取權限 SDDL 轉換成 PSCustomObject `-Type`

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

第一個命令會使用 `Get-Acl` Cmdlet 來取得 HKLM： \ SOFTWARE\Microsoft\ 金鑰的安全描述項，並將其儲存在變數中。

第二個命令會使用 `ConvertFrom-SddlString` Cmdlet 來取得 sddl 字串的文字標記法，此物件包含在代表安全描述項之物件的 sddl 屬性中。

它不會使用 `-Type` 參數，因此顯示的存取權限是針對檔案系統。

第三個命令 `ConvertFrom-SddlString` 會使用 Cmdlet 搭配 `-Type` 參數，因此傳回的存取權限是針對登錄。

## PARAMETERS

### -Sddl

指定以 SDDL 語法表示安全描述項的字串。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

指定 SDDL 字串代表的許可權類型。

此參數可接受的值為：

- FileSystemRights
- RegistryRights
- ActiveDirectoryRights
- MutexRights
- SemaphoreRights
- CryptoKeyRights
- EventWaitHandleRights

根據預設，Cmdlet 會使用檔案系統許可權。

PowerShell Core 不支援 CryptoKeyRights 和 ActiveDirectoryRights。

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將 SDDL 字串傳送至 `ConvertFrom-SddlString` 。

## 輸出

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

## 相關連結

[安全描述項定義語言](/windows/win32/secauthz/security-descriptor-definition-language)
