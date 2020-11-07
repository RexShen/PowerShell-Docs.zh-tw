---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.x&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 394e8c1b18d7ba0f4b65e1681faffe795592b97d
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347664"
---
# Unprotect-CmsMessage

## 概要
使用密碼編譯訊息語法格式來解密已加密的內容。

## SYNTAX

### ByWinEvent (預設) 

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### ByContent

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByPath

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## DESCRIPTION

`Unprotect-CmsMessage`Cmdlet 會將使用密碼編譯訊息語法加密的內容解密 (CMS) 格式。

CMS Cmdlet 支援使用 IETF 標準格式加密和解密內容，以進行密碼編譯保護訊息，如 [>rfc5652](https://tools.ietf.org/html/rfc5652)所述。

CMS 加密標準會使用公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 和用於解密內容的金錀 (私密金鑰) 是分開的。 公開金鑰可以廣泛共用，並非機密資料。 如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。 如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。

`Unprotect-CmsMessage` 解密已加密 CMS 格式的內容。 您可以執行此 Cmdlet 來解密您透過執行指令程式加密的內容 `Protect-CmsMessage` 。 您可以指定要解密為字串的內容、加密事件記錄檔記錄識別碼或加密內容的路徑。 Cmdlet 會傳回 `Unprotect-CmsMessage` 解密的內容。

> [!NOTE]
> 此 Cmdlet 僅適用于 Windows。

## 範例

### 範例1：解密訊息

在下列範例中，您會解密位於常值路徑的內容 `C:\Users\Test\Documents\PowerShell` 。 針對所需參數的值，此範例會使用 **用來執行** 加密的憑證指紋。 結果就是解密的訊息：「嘗試 new Break All 命令」。

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -EventLogRecord

指定代表 CMS 加密作業的事件記錄識別碼。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -IncludeCoNtext

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

### -LiteralPath

指定您要解密之加密內容的路徑。 與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
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
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -To

指定一或多個 CMS 訊息收件者，以下列任何格式識別：

- 實際的憑證 (擷取自憑證提供者)。
- 包含憑證之檔案的路徑。
- 包含憑證的目錄路徑。
- 憑證的指紋 (用於在憑證存放區尋找)。
- 憑證的主體名稱 (用於在憑證存放區尋找)。

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### EventLogRecord 或 System.string （系統）

您可以使用管線將包含加密內容的物件傳送至 `Unprotect-CmsMessage` 。

## 輸出

### System.String

未加密的訊息。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

## 相關連結

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Protect-CmsMessage](Protect-CmsMessage.md)
