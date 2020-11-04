---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: eaabf4e45a9441a479059513a428f2d87430dd2a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204947"
---
# <span data-ttu-id="80240-103">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="80240-103">Unprotect-CmsMessage</span></span>

## <span data-ttu-id="80240-104">概要</span><span class="sxs-lookup"><span data-stu-id="80240-104">SYNOPSIS</span></span>
<span data-ttu-id="80240-105">使用密碼編譯訊息語法格式來解密已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="80240-105">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="80240-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="80240-106">SYNTAX</span></span>

### <span data-ttu-id="80240-107">ByWinEvent (預設) </span><span class="sxs-lookup"><span data-stu-id="80240-107">ByWinEvent (Default)</span></span>

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="80240-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="80240-108">ByContent</span></span>

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="80240-109">ByPath</span><span class="sxs-lookup"><span data-stu-id="80240-109">ByPath</span></span>

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="80240-110">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="80240-110">ByLiteralPath</span></span>

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="80240-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="80240-111">DESCRIPTION</span></span>

<span data-ttu-id="80240-112">`Unprotect-CmsMessage`Cmdlet 會將使用密碼編譯訊息語法加密的內容解密 (CMS) 格式。</span><span class="sxs-lookup"><span data-stu-id="80240-112">The `Unprotect-CmsMessage` cmdlet decrypts content that has been encrypted by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="80240-113">CMS Cmdlet 支援使用 IETF 標準格式加密和解密內容，以進行密碼編譯保護訊息，如 [>rfc5652](https://tools.ietf.org/html/rfc5652)所述。</span><span class="sxs-lookup"><span data-stu-id="80240-113">The CMS cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="80240-114">CMS 加密標準會使用公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 和用於解密內容的金錀 (私密金鑰) 是分開的。</span><span class="sxs-lookup"><span data-stu-id="80240-114">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="80240-115">公開金鑰可以廣泛共用，並非機密資料。</span><span class="sxs-lookup"><span data-stu-id="80240-115">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="80240-116">如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。</span><span class="sxs-lookup"><span data-stu-id="80240-116">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="80240-117">如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。</span><span class="sxs-lookup"><span data-stu-id="80240-117">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="80240-118">`Unprotect-CmsMessage` 解密已加密 CMS 格式的內容。</span><span class="sxs-lookup"><span data-stu-id="80240-118">`Unprotect-CmsMessage` decrypts content that has been encrypted in CMS format.</span></span> <span data-ttu-id="80240-119">您可以執行此 Cmdlet 來解密您透過執行指令程式加密的內容 `Protect-CmsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="80240-119">You can run this cmdlet to decrypt content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="80240-120">您可以指定要解密為字串的內容、加密事件記錄檔記錄識別碼或加密內容的路徑。</span><span class="sxs-lookup"><span data-stu-id="80240-120">You can specify content that you want to decrypt as a string, by the encryption event log record ID number, or by path to the encrypted content.</span></span> <span data-ttu-id="80240-121">Cmdlet 會傳回 `Unprotect-CmsMessage` 解密的內容。</span><span class="sxs-lookup"><span data-stu-id="80240-121">The `Unprotect-CmsMessage` cmdlet returns the decrypted content.</span></span>

<span data-ttu-id="80240-122">已在 PowerShell 7.1 中新增 Linux 和 macOS 的支援。</span><span class="sxs-lookup"><span data-stu-id="80240-122">Support for Linux and macOS was added in PowerShell 7.1.</span></span>

## <span data-ttu-id="80240-123">範例</span><span class="sxs-lookup"><span data-stu-id="80240-123">EXAMPLES</span></span>

### <span data-ttu-id="80240-124">範例1：解密訊息</span><span class="sxs-lookup"><span data-stu-id="80240-124">Example 1: Decrypt a message</span></span>

<span data-ttu-id="80240-125">在下列範例中，您會解密位於常值路徑的內容 `C:\Users\Test\Documents\PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="80240-125">In the following example, you decrypt content that is located at the literal path `C:\Users\Test\Documents\PowerShell`.</span></span> <span data-ttu-id="80240-126">針對所需參數的值，此範例會使用 **用來執行** 加密的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="80240-126">For the value of the required **To** parameter, this example uses the thumbprint of the certificate that was used to perform the encryption.</span></span> <span data-ttu-id="80240-127">結果就是解密的訊息：「嘗試 new Break All 命令」。</span><span class="sxs-lookup"><span data-stu-id="80240-127">The decrypted message, "Try the new Break All command," is the result.</span></span>

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

## <span data-ttu-id="80240-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="80240-128">PARAMETERS</span></span>

### <span data-ttu-id="80240-129">-Content</span><span class="sxs-lookup"><span data-stu-id="80240-129">-Content</span></span>

<span data-ttu-id="80240-130">指定加密的字串，或包含加密字串的變數。</span><span class="sxs-lookup"><span data-stu-id="80240-130">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

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

### <span data-ttu-id="80240-131">-EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="80240-131">-EventLogRecord</span></span>

<span data-ttu-id="80240-132">指定代表 CMS 加密作業的事件記錄識別碼。</span><span class="sxs-lookup"><span data-stu-id="80240-132">Specifies an event log record ID that represents a CMS encryption operation.</span></span>

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

### <span data-ttu-id="80240-133">-IncludeCoNtext</span><span class="sxs-lookup"><span data-stu-id="80240-133">-IncludeContext</span></span>

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

### <span data-ttu-id="80240-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="80240-134">-LiteralPath</span></span>

<span data-ttu-id="80240-135">指定您要解密之加密內容的路徑。</span><span class="sxs-lookup"><span data-stu-id="80240-135">Specifies the path to encrypted content that you want to decrypt.</span></span> <span data-ttu-id="80240-136">與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="80240-136">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="80240-137">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="80240-137">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="80240-138">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="80240-138">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="80240-139">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="80240-139">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="80240-140">-Path</span><span class="sxs-lookup"><span data-stu-id="80240-140">-Path</span></span>

<span data-ttu-id="80240-141">指定您要解密之加密內容的路徑。</span><span class="sxs-lookup"><span data-stu-id="80240-141">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="80240-142">-To</span><span class="sxs-lookup"><span data-stu-id="80240-142">-To</span></span>

<span data-ttu-id="80240-143">指定一或多個 CMS 訊息收件者，以下列任何格式識別：</span><span class="sxs-lookup"><span data-stu-id="80240-143">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="80240-144">實際的憑證 (擷取自憑證提供者)。</span><span class="sxs-lookup"><span data-stu-id="80240-144">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="80240-145">包含憑證之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="80240-145">Path to the a file containing the certificate.</span></span>
- <span data-ttu-id="80240-146">包含憑證的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="80240-146">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="80240-147">憑證的指紋 (用於在憑證存放區尋找)。</span><span class="sxs-lookup"><span data-stu-id="80240-147">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="80240-148">憑證的主體名稱 (用於在憑證存放區尋找)。</span><span class="sxs-lookup"><span data-stu-id="80240-148">Subject name of the certificate (used to look in the certificate store).</span></span>

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

### <span data-ttu-id="80240-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80240-149">CommonParameters</span></span>

<span data-ttu-id="80240-150">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="80240-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80240-151">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="80240-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="80240-152">輸入</span><span class="sxs-lookup"><span data-stu-id="80240-152">INPUTS</span></span>

### <span data-ttu-id="80240-153">EventLogRecord 或 System.string （系統）</span><span class="sxs-lookup"><span data-stu-id="80240-153">System.Diagnostics.Eventing.Reader.EventLogRecord or System.String</span></span>

<span data-ttu-id="80240-154">您可以使用管線將包含加密內容的物件傳送至 `Unprotect-CmsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="80240-154">You can pipe an object containing encrypted content to `Unprotect-CmsMessage`.</span></span>

## <span data-ttu-id="80240-155">輸出</span><span class="sxs-lookup"><span data-stu-id="80240-155">OUTPUTS</span></span>

### <span data-ttu-id="80240-156">System.String</span><span class="sxs-lookup"><span data-stu-id="80240-156">System.String</span></span>

<span data-ttu-id="80240-157">未加密的訊息。</span><span class="sxs-lookup"><span data-stu-id="80240-157">The unencrypted message.</span></span>

## <span data-ttu-id="80240-158">注意</span><span class="sxs-lookup"><span data-stu-id="80240-158">NOTES</span></span>

## <span data-ttu-id="80240-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="80240-159">RELATED LINKS</span></span>

[<span data-ttu-id="80240-160">about_Providers</span><span class="sxs-lookup"><span data-stu-id="80240-160">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="80240-161">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="80240-161">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="80240-162">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="80240-162">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)
