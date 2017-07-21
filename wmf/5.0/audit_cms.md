---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 9556f0d9a12807cbfe38aaade6798088f051596d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="5fe59-102">密碼編譯訊息語法 (CMS) Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fe59-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="5fe59-103">密碼編譯訊息語法 Cmdlet 支援使用 IETF 標準格式加密和解密內容，進行密碼編譯保護訊息，如 [RFC5652](http://tools.ietf.org/html/rfc5652) 所述。</span><span class="sxs-lookup"><span data-stu-id="5fe59-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](http://tools.ietf.org/html/rfc5652).</span></span>

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

<span data-ttu-id="5fe59-104">CMS 加密標準實作公開金錀密碼編譯，這裡用於加密內容的金錀 (*公開金錀*) 和用於解密內容的金錀 (*私密金鑰*) 是分開的。</span><span class="sxs-lookup"><span data-stu-id="5fe59-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="5fe59-105">公開金鑰可以廣泛共用，並非機密資料。</span><span class="sxs-lookup"><span data-stu-id="5fe59-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="5fe59-106">如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。</span><span class="sxs-lookup"><span data-stu-id="5fe59-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="5fe59-107">如需公開金鑰加密的詳細資訊，請參閱︰<http://en.wikipedia.org/wiki/Public-key_cryptography>。</span><span class="sxs-lookup"><span data-stu-id="5fe59-107">For more information about Public Key Cryptography, see: <http://en.wikipedia.org/wiki/Public-key_cryptography>.</span></span>

<span data-ttu-id="5fe59-108">為能在 PowerShell 中辨識，加密憑證需要唯一的金鑰使用方法識別碼 (EKU) 來辨識其為資料加密憑證 (就像「程式碼簽署」、「加密郵件」的識別碼一樣)。</span><span class="sxs-lookup"><span data-stu-id="5fe59-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="5fe59-109">下例示範建立適用於文件加密的憑證：</span><span class="sxs-lookup"><span data-stu-id="5fe59-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

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

<span data-ttu-id="5fe59-110">然後執行：</span><span class="sxs-lookup"><span data-stu-id="5fe59-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="5fe59-111">您現在可以加密和解密內容：</span><span class="sxs-lookup"><span data-stu-id="5fe59-111">And you can now encrypt and decrypt content:</span></span>

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

<span data-ttu-id="5fe59-112">任何 **CMSMessageRecipient** 類型的參數都支援以下格式的識別碼：</span><span class="sxs-lookup"><span data-stu-id="5fe59-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="5fe59-113">實際的憑證 (自憑證提供者處擷取)</span><span class="sxs-lookup"><span data-stu-id="5fe59-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="5fe59-114">包含憑證的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="5fe59-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="5fe59-115">包含憑證的目錄路徑</span><span class="sxs-lookup"><span data-stu-id="5fe59-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="5fe59-116">憑證的指紋 (用於在憑證存放區尋找)</span><span class="sxs-lookup"><span data-stu-id="5fe59-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="5fe59-117">憑證的主體名稱 (用於在憑證存放區尋找)</span><span class="sxs-lookup"><span data-stu-id="5fe59-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="5fe59-118">若要檢視憑證提供者的文件加密憑證，您可以使用 **-DocumentEncryptionCert** 動態參數︰</span><span class="sxs-lookup"><span data-stu-id="5fe59-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```

