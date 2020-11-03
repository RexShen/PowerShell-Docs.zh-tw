---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: b76fc092046a29dcad52f755794fd55dd84ac675
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "93205248"
---
# Read-Host

## 概要
從主控台讀取輸入的一行。

## SYNTAX

### AsString (預設值)

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### AsSecureString

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## DESCRIPTION

`Read-Host`Cmdlet 會從主控台讀取輸入的一行。 您可以使用它來提示使用者輸入。 由於您可以將輸入儲存成安全字串，因此您可以使用這個 Cmdlet 來提示使用者輸入安全資料 (例如密碼) 和共用的資料。

## 範例

### 範例1：將主控台輸入儲存至變數

此範例會顯示 "請輸入您的年齡：" 字串做為提示。 當輸入值並按下 Enter 鍵時，值會儲存在 `$Age` 變數中。

```powershell
$Age = Read-Host "Please enter your age"
```

### 範例2：將主控台輸入儲存為安全字串

此範例會顯示 "Enter a Password：" 字串做為提示。 輸入值時，星號 (`*`) 會出現在主控台上，以取代輸入。 按下 Enter 鍵時，該值會以 **SecureString** 物件的形式儲存在變數中 `$pwd_secure_string` 。

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### 範例3：遮罩輸入和純文字字串

此範例會顯示 "Enter a Password：" 字串做為提示。 輸入值時，星號 (`*`) 會出現在主控台上，以取代輸入。 按下 Enter 鍵時，該值會以純文字 **字串** 物件的形式儲存在 `$pwd_string` 變數中。

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## PARAMETERS

### -AsSecureString

指出此 Cmdlet 會顯示星號 (`*`) 來取代使用者輸入的字元。 當您使用此參數時，Cmdlet 的輸出 `Read-Host` 會是 **SecureString** 物件， ( **SecureString** ) 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaskInput

指出此 Cmdlet 會顯示星號 (`*`) 來取代使用者輸入的字元。 當您使用此參數時，Cmdlet 的輸出 `Read-Host` 是 **字串** 物件。
這可讓您安全地提示輸入以純文字格式傳回的密碼，而不是 **SecureString** 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Prompt

指定提示的文字。
輸入字串。
如果字串包含空格，請將它括在引號中。
PowerShell `:` 會在您輸入的文字中附加冒號 () 。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.String 或 System.Security.SecureString

如果使用 **AsSecureString** 參數，則會傳回 `Read-Host` **SecureString** 。 否則，它會傳回字串。

## 注意

## 相關連結

[Clear-Host](../microsoft.powershell.core/clear-host.md)

[Get-Host](Get-Host.md)

[Write-Host](Write-Host.md)

[ConvertFrom-SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
