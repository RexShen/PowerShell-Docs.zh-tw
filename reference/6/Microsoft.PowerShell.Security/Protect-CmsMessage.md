---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: 8cef49e068a051225e5eac188f495c71cfaa35f5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344850"
---
# <span data-ttu-id="e0733-103">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="e0733-103">Protect-CmsMessage</span></span>

## <span data-ttu-id="e0733-104">概要</span><span class="sxs-lookup"><span data-stu-id="e0733-104">SYNOPSIS</span></span>
<span data-ttu-id="e0733-105">使用密碼編譯訊息語法格式來加密內容。</span><span class="sxs-lookup"><span data-stu-id="e0733-105">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="e0733-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0733-106">SYNTAX</span></span>

### <span data-ttu-id="e0733-107">ByContent (預設值)</span><span class="sxs-lookup"><span data-stu-id="e0733-107">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="e0733-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="e0733-108">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="e0733-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="e0733-109">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="e0733-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0733-110">DESCRIPTION</span></span>

<span data-ttu-id="e0733-111">此 `Protect-CmsMessage` Cmdlet 會使用 (CMS) 格式的密碼編譯訊息語法來加密內容。</span><span class="sxs-lookup"><span data-stu-id="e0733-111">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="e0733-112">CMS Cmdlet 支援使用 IETF 格式來加密和解密內容，如 [>rfc5652](https://tools.ietf.org/html/rfc5652.html)所述。</span><span class="sxs-lookup"><span data-stu-id="e0733-112">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="e0733-113">CMS 加密標準會使用公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 和用於解密內容的金錀 (私密金鑰) 是分開的。</span><span class="sxs-lookup"><span data-stu-id="e0733-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="e0733-114">公開金鑰可以廣泛共用，並非機密資料。</span><span class="sxs-lookup"><span data-stu-id="e0733-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="e0733-115">如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。</span><span class="sxs-lookup"><span data-stu-id="e0733-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="e0733-116">如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。</span><span class="sxs-lookup"><span data-stu-id="e0733-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="e0733-117">您 `Protect-CmsMessage` 必須先設定加密憑證，才可以執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e0733-117">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="e0733-118">若要在 PowerShell 中辨識，加密憑證需要唯一的擴充金鑰使用方法 ([EKU](/windows/desktop/SecCrypto/eku)) 識別碼，以將其識別為資料加密憑證 (例如程式碼簽署和加密郵件) 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e0733-118">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="e0733-119">如需適用於文件加密的憑證範例，請參閱本主題的範例 1。</span><span class="sxs-lookup"><span data-stu-id="e0733-119">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="e0733-120">此 Cmdlet 僅適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="e0733-120">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="e0733-121">範例</span><span class="sxs-lookup"><span data-stu-id="e0733-121">EXAMPLES</span></span>

### <span data-ttu-id="e0733-122">範例 1︰建立憑證來加密內容</span><span class="sxs-lookup"><span data-stu-id="e0733-122">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="e0733-123">您 `Protect-CmsMessage` 必須先建立加密憑證，才可以執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e0733-123">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="e0733-124">使用下列文字，將主旨行中的名稱變更為您的名稱、電子郵件或其他識別碼，然後將憑證儲存在檔案 (例如，如 `DocumentEncryption.inf` 下列範例所示) 。</span><span class="sxs-lookup"><span data-stu-id="e0733-124">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

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

### <span data-ttu-id="e0733-125">範例 2︰加密透過電子郵件傳送的訊息</span><span class="sxs-lookup"><span data-stu-id="e0733-125">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="e0733-126">在下列範例中，您會將訊息傳送至 Cmdlet 以加密訊息 "Hello World"，然後將 `Protect-CmsMessage` 加密的訊息儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e0733-126">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="e0733-127">**To** 參數會使用憑證中主旨行的值。</span><span class="sxs-lookup"><span data-stu-id="e0733-127">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="e0733-128">範例 3︰檢視文件加密憑證</span><span class="sxs-lookup"><span data-stu-id="e0733-128">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="e0733-129">若要在憑證提供者中查看檔加密憑證，您可以新增 **>documentencryptioncert** 動態參數 [get-childitem](../Microsoft.PowerShell.Management/Get-ChildItem.md)，只有在憑證提供者載入時才能使用。</span><span class="sxs-lookup"><span data-stu-id="e0733-129">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="e0733-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e0733-130">PARAMETERS</span></span>

### <span data-ttu-id="e0733-131">-Content</span><span class="sxs-lookup"><span data-stu-id="e0733-131">-Content</span></span>

<span data-ttu-id="e0733-132">指定包含您要加密之內容的 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="e0733-132">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="e0733-133">例如，您可以加密事件訊息的內容，然後使用包含訊息 (的變數 `$Event` ，在此範例中) 做為 **content** 參數的值： `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` 。</span><span class="sxs-lookup"><span data-stu-id="e0733-133">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="e0733-134">您也可以使用 `Get-Content` Cmdlet 來取得檔案的內容，例如 Microsoft Word 檔，並將內容儲存在您用來作為 **content** 參數值的變數中。</span><span class="sxs-lookup"><span data-stu-id="e0733-134">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

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

### <span data-ttu-id="e0733-135">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e0733-135">-LiteralPath</span></span>

<span data-ttu-id="e0733-136">指定您想要加密的內容路徑。</span><span class="sxs-lookup"><span data-stu-id="e0733-136">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="e0733-137">與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="e0733-137">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e0733-138">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e0733-138">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e0733-139">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="e0733-139">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e0733-140">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="e0733-140">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e0733-141">-OutFile</span><span class="sxs-lookup"><span data-stu-id="e0733-141">-OutFile</span></span>

<span data-ttu-id="e0733-142">指定您要傳送加密內容的檔案路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e0733-142">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

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

### <span data-ttu-id="e0733-143">-Path</span><span class="sxs-lookup"><span data-stu-id="e0733-143">-Path</span></span>

<span data-ttu-id="e0733-144">指定您想要加密的內容路徑。</span><span class="sxs-lookup"><span data-stu-id="e0733-144">Specifies the path to content that you want to encrypt.</span></span>

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

### <span data-ttu-id="e0733-145">-To</span><span class="sxs-lookup"><span data-stu-id="e0733-145">-To</span></span>

<span data-ttu-id="e0733-146">指定一或多個 CMS 訊息收件者，以下列任何格式識別：</span><span class="sxs-lookup"><span data-stu-id="e0733-146">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="e0733-147">實際的憑證 (擷取自憑證提供者)。</span><span class="sxs-lookup"><span data-stu-id="e0733-147">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="e0733-148">包含憑證的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="e0733-148">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="e0733-149">包含憑證的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="e0733-149">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="e0733-150">憑證的指紋 (用於在憑證存放區尋找)。</span><span class="sxs-lookup"><span data-stu-id="e0733-150">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="e0733-151">憑證的主體名稱 (用於在憑證存放區尋找)。</span><span class="sxs-lookup"><span data-stu-id="e0733-151">Subject name of the certificate (used to look in the certificate store).</span></span>

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

### <span data-ttu-id="e0733-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0733-152">CommonParameters</span></span>

<span data-ttu-id="e0733-153">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="e0733-153">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="e0733-154">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e0733-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e0733-155">輸入</span><span class="sxs-lookup"><span data-stu-id="e0733-155">INPUTS</span></span>

## <span data-ttu-id="e0733-156">輸出</span><span class="sxs-lookup"><span data-stu-id="e0733-156">OUTPUTS</span></span>

## <span data-ttu-id="e0733-157">注意</span><span class="sxs-lookup"><span data-stu-id="e0733-157">NOTES</span></span>

<span data-ttu-id="e0733-158">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="e0733-158">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="e0733-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="e0733-159">RELATED LINKS</span></span>

[<span data-ttu-id="e0733-160">about_Providers</span><span class="sxs-lookup"><span data-stu-id="e0733-160">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="e0733-161">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="e0733-161">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="e0733-162">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="e0733-162">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
