---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 1642f30579e71835233431438172ffc1000c4203
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201751"
---
# Get-PfxCertificate

## 概要
取得電腦上 PFX 憑證檔案的相關資訊。

## SYNTAX

### ByPath (預設值)

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### ByLiteralPath

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-PfxCertificate`Cmdlet 會取得代表每個指定 PFX 憑證檔案的物件。
PFX 檔案包含憑證和私密金鑰。

## 範例

### 範例1：取得 PFX 憑證

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

此命令會取得系統上的 Test .pfx 憑證檔案的相關資訊。

### 範例2：從遠端電腦取得 PFX 憑證

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

此命令會從 Server01 遠端電腦取得 PFX 憑證檔案。 它是用 `Invoke-Command` 來 `Get-PfxCertificate` 從遠端執行命令。

如果 PFX 憑證檔案未受密碼保護，的 **Authentication** 參數值 `Invoke-Command` 必須是 CredSSP。

## PARAMETERS

### -FilePath

指定受保護檔案之 PFX 檔案的完整路徑。 如果您指定此參數的值，則不需要 `-FilePath` 在命令列輸入。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

受保護檔案之 PFX 檔案的完整路徑。 **LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoPromptForPassword

抑制提示輸入密碼。

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

### -Password

指定存取憑證檔案所需的密碼 `.pfx` 。

此參數是在 PowerShell 6.1 中引進。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含檔案路徑的字串傳送至 `Get-PfxCertificate` 。

## 輸出

### System.Security.Cryptography.X509Certificates.X509Certificate2

`Get-PfxCertificate` 針對取得的每個憑證傳回物件。

## 注意

使用 `Invoke-Command` `Get-PfxCertificate` 指令程式從遠端執行命令，且 PFX 憑證檔案未受密碼保護時，的 **Authentication** 參數值 `Invoke-Command` 必須是 CredSSP。

## 相關連結

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)
