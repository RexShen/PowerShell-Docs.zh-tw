---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: bca0f75ac371fe18d5a35f5c57572f415922d890
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201372"
---
# Protect-CmsMessage

## 概要
使用密碼編譯訊息語法格式來加密內容。

## SYNTAX

### ByContent (預設值)

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### ByPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### ByLiteralPath

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Protect-CmsMessage` Cmdlet 會使用 (CMS) 格式的密碼編譯訊息語法來加密內容。

CMS Cmdlet 支援使用 IETF 格式來加密和解密內容，如 [>rfc5652](https://tools.ietf.org/html/rfc5652.html)所述。

CMS 加密標準會使用公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 和用於解密內容的金錀 (私密金鑰) 是分開的。 公開金鑰可以廣泛共用，並非機密資料。 如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。 如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。

您 `Protect-CmsMessage` 必須先設定加密憑證，才可以執行此 Cmdlet。
若要在 PowerShell 中辨識，加密憑證需要唯一的擴充金鑰使用方法 ([EKU](/windows/desktop/SecCrypto/eku)) 識別碼，以將其識別為資料加密憑證 (例如程式碼簽署和加密郵件) 的識別碼。 如需適用於文件加密的憑證範例，請參閱本主題的範例 1。

> [!NOTE]
> 此 Cmdlet 僅適用于 Windows。

## 範例

### 範例 1︰建立憑證來加密內容

您 `Protect-CmsMessage` 必須先建立加密憑證，才可以執行此 Cmdlet。 使用下列文字，將主旨行中的名稱變更為您的名稱、電子郵件或其他識別碼，然後將憑證儲存在檔案 (例如，如 `DocumentEncryption.inf` 下列範例所示) 。

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### 範例 2︰加密透過電子郵件傳送的訊息

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

在下列範例中，您會將訊息傳送至 Cmdlet 以加密訊息 "Hello World"，然後將 `Protect-CmsMessage` 加密的訊息儲存在變數中。 **To** 參數會使用憑證中主旨行的值。

### 範例 3︰檢視文件加密憑證

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

若要在憑證提供者中查看檔加密憑證，您可以新增 **>documentencryptioncert** 動態參數 [get-childitem](../Microsoft.PowerShell.Management/Get-ChildItem.md)，只有在憑證提供者載入時才能使用。

## PARAMETERS

### -Content

指定包含您要加密之內容的 **PSObject** 。 例如，您可以加密事件訊息的內容，然後使用包含訊息 (的變數 `$Event` ，在此範例中) 做為 **content** 參數的值： `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` 。 您也可以使用 `Get-Content` Cmdlet 來取得檔案的內容，例如 Microsoft Word 檔，並將內容儲存在您用來作為 **content** 參數值的變數中。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定您想要加密的內容路徑。 與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

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

### -OutFile

指定您要傳送加密內容的檔案路徑和檔案名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定您想要加密的內容路徑。

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

### -To

指定一或多個 CMS 訊息收件者，以下列任何格式識別：

- 實際的憑證 (擷取自憑證提供者)。
- 包含憑證的檔案路徑。
- 包含憑證的目錄路徑。
- 憑證的指紋 (用於在憑證存放區尋找)。
- 憑證的主體名稱 (用於在憑證存放區尋找)。

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

## 輸出

## 注意

## 相關連結

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-CmsMessage](Get-CmsMessage.md)

[Unprotect-CmsMessage](Unprotect-CmsMessage.md)
