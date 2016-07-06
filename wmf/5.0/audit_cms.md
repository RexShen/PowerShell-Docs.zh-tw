# 密碼編譯訊息語法 (CMS) Cmdlet

密碼編譯訊息語法 Cmdlet 支援使用 IETF 標準格式加密和解密內容，進行密碼編譯保護訊息，如 [RFC5652](http://tools.ietf.org/html/rfc5652) 所述。

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

CMS 加密標準實作公開金錀密碼編譯，這裡用於加密內容的金錀 (*公開金錀*) 和用於解密內容的金錀 (*私密金鑰*) 是分開的。

公開金鑰可以廣泛共用，並非機密資料。 如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。 如需公開金鑰加密的詳細資訊，請參閱︰<http://en.wikipedia.org/wiki/Public-key_cryptography>。

為能在 PowerShell 中辨識，加密憑證需要唯一的金鑰使用方法識別碼 (EKU) 來辨識其為資料加密憑證 (就像「程式碼簽署」、「加密郵件」的識別碼一樣)。

下例示範建立適用於文件加密的憑證：

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

然後執行：
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

您現在可以加密和解密內容：

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

任何 **CMSMessageRecipient** 類型的參數都支援以下格式的識別碼：
- 實際的憑證 (自憑證提供者處擷取)
- 包含憑證的檔案路徑
- 包含憑證的目錄路徑
- 憑證的指紋 (用於在憑證存放區尋找)
- 憑證的主體名稱 (用於在憑證存放區尋找)

若要檢視憑證提供者的文件加密憑證，您可以使用 **-DocumentEncryptionCert** 動態參數︰

```powershell
dir -DocumentEncryptionCert
```

<!--HONumber=Jun16_HO4-->


