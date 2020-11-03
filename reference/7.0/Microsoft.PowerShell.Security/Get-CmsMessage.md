---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: b90059cd735e26eceb66d211533abbe25894d0ec
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201191"
---
# Get-CmsMessage

## 概要
使用密碼編譯訊息語法格式來取得已加密的內容。

## SYNTAX

### ByContent

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### ByPath

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### ByLiteralPath

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## DESCRIPTION

指令 `Get-CmsMessage` 程式會使用 (CMS) 格式的密碼編譯訊息語法，取得已加密的內容。

CMS Cmdlet 支援使用 IETF 格式的內容加密和解密以進行密碼編譯保護訊息，如 [>rfc5652](https://tools.ietf.org/html/rfc5652)所述。

CMS 加密標準會使用公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 和用於解密內容的金錀 (私密金鑰) 是分開的。 公開金鑰可以廣泛共用，並非機密資料。 如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。 如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。

`Get-CmsMessage` 取得已加密 CMS 格式的內容。 它不會將內容解密或取消保護。 您可以執行此 Cmdlet 來取得您透過執行指令程式加密的內容 `Protect-CmsMessage` 。 您可以指定要解密為字串的內容，或指定為加密內容的路徑。 您可以使用管線將的結果傳送至來 `Get-CmsMessage` `Unprotect-CmsMessage` 解密內容，前提是您擁有用來加密內容的檔加密憑證的相關資訊。

> [!NOTE]
> 此 Cmdlet 僅適用于 Windows。

## 範例

### 範例1：取得加密的內容

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

此命令會取得位於 C:\Users\Test\Documents\PowerShell\Future_Plans.txt 的加密內容。

### 範例2：將加密的內容輸送至 Unprotect-CmsMessage

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

此命令會將 Cmdlet 的結果 `Get-CmsMessage` 從範例1傳送至 `Unprotect-CmsMessage` ，以將訊息解密並以純文字讀取。 在此情況下， **To** 參數的值是加密憑證之主旨行的值。 結果就是解密的訊息：「嘗試 new Break All 命令」。

## PARAMETERS

### -Content

指定加密的字串，或包含加密字串的變數。

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定您想要取得之加密內容的路徑。 與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請用單引號括住每一個字元。
單引號指示 PowerShell 不要將括住的字元解讀為 escape 字元。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定您要解密之加密內容的路徑。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Protect-CmsMessage](Protect-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)
