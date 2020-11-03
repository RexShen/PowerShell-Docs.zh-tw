---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: 30e70549b648f7fb63bb250744cf52f0979c201f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203780"
---
# <span data-ttu-id="cf897-103">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="cf897-103">Get-CmsMessage</span></span>

## <span data-ttu-id="cf897-104">概要</span><span class="sxs-lookup"><span data-stu-id="cf897-104">SYNOPSIS</span></span>
<span data-ttu-id="cf897-105">使用密碼編譯訊息語法格式來取得已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="cf897-105">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="cf897-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf897-106">SYNTAX</span></span>

### <span data-ttu-id="cf897-107">ByContent</span><span class="sxs-lookup"><span data-stu-id="cf897-107">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="cf897-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="cf897-108">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="cf897-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="cf897-109">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="cf897-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cf897-110">DESCRIPTION</span></span>

<span data-ttu-id="cf897-111">指令 `Get-CmsMessage` 程式會使用 (CMS) 格式的密碼編譯訊息語法，取得已加密的內容。</span><span class="sxs-lookup"><span data-stu-id="cf897-111">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="cf897-112">CMS Cmdlet 支援使用 IETF 格式的內容加密和解密以進行密碼編譯保護訊息，如 [>rfc5652](https://tools.ietf.org/html/rfc5652)所述。</span><span class="sxs-lookup"><span data-stu-id="cf897-112">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="cf897-113">CMS 加密標準會使用公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 和用於解密內容的金錀 (私密金鑰) 是分開的。</span><span class="sxs-lookup"><span data-stu-id="cf897-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="cf897-114">公開金鑰可以廣泛共用，並非機密資料。</span><span class="sxs-lookup"><span data-stu-id="cf897-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="cf897-115">如有任何內容以此公開金鑰加密，只有您的私密金鑰可以解密。</span><span class="sxs-lookup"><span data-stu-id="cf897-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="cf897-116">如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。</span><span class="sxs-lookup"><span data-stu-id="cf897-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="cf897-117">`Get-CmsMessage` 取得已加密 CMS 格式的內容。</span><span class="sxs-lookup"><span data-stu-id="cf897-117">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="cf897-118">它不會將內容解密或取消保護。</span><span class="sxs-lookup"><span data-stu-id="cf897-118">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="cf897-119">您可以執行此 Cmdlet 來取得您透過執行指令程式加密的內容 `Protect-CmsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="cf897-119">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="cf897-120">您可以指定要解密為字串的內容，或指定為加密內容的路徑。</span><span class="sxs-lookup"><span data-stu-id="cf897-120">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="cf897-121">您可以使用管線將的結果傳送至來 `Get-CmsMessage` `Unprotect-CmsMessage` 解密內容，前提是您擁有用來加密內容的檔加密憑證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cf897-121">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

> [!NOTE]
> <span data-ttu-id="cf897-122">此 Cmdlet 僅適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="cf897-122">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="cf897-123">範例</span><span class="sxs-lookup"><span data-stu-id="cf897-123">EXAMPLES</span></span>

### <span data-ttu-id="cf897-124">範例1：取得加密的內容</span><span class="sxs-lookup"><span data-stu-id="cf897-124">Example 1: Get encrypted content</span></span>

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

<span data-ttu-id="cf897-125">此命令會取得位於 C:\Users\Test\Documents\PowerShell\Future_Plans.txt 的加密內容。</span><span class="sxs-lookup"><span data-stu-id="cf897-125">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="cf897-126">範例2：將加密的內容輸送至 Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="cf897-126">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="cf897-127">此命令會將 Cmdlet 的結果 `Get-CmsMessage` 從範例1傳送至 `Unprotect-CmsMessage` ，以將訊息解密並以純文字讀取。</span><span class="sxs-lookup"><span data-stu-id="cf897-127">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="cf897-128">在此情況下， **To** 參數的值是加密憑證之主旨行的值。</span><span class="sxs-lookup"><span data-stu-id="cf897-128">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="cf897-129">結果就是解密的訊息：「嘗試 new Break All 命令」。</span><span class="sxs-lookup"><span data-stu-id="cf897-129">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="cf897-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf897-130">PARAMETERS</span></span>

### <span data-ttu-id="cf897-131">-Content</span><span class="sxs-lookup"><span data-stu-id="cf897-131">-Content</span></span>

<span data-ttu-id="cf897-132">指定加密的字串，或包含加密字串的變數。</span><span class="sxs-lookup"><span data-stu-id="cf897-132">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

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

### <span data-ttu-id="cf897-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cf897-133">-LiteralPath</span></span>

<span data-ttu-id="cf897-134">指定您想要取得之加密內容的路徑。</span><span class="sxs-lookup"><span data-stu-id="cf897-134">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="cf897-135">與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="cf897-135">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="cf897-136">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf897-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="cf897-137">如果路徑包含 escape 字元，請用單引號括住每一個字元。</span><span class="sxs-lookup"><span data-stu-id="cf897-137">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="cf897-138">單引號指示 PowerShell 不要將括住的字元解讀為 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="cf897-138">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

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

### <span data-ttu-id="cf897-139">-Path</span><span class="sxs-lookup"><span data-stu-id="cf897-139">-Path</span></span>

<span data-ttu-id="cf897-140">指定您要解密之加密內容的路徑。</span><span class="sxs-lookup"><span data-stu-id="cf897-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

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

### <span data-ttu-id="cf897-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf897-141">CommonParameters</span></span>

<span data-ttu-id="cf897-142">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cf897-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf897-143">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cf897-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf897-144">輸入</span><span class="sxs-lookup"><span data-stu-id="cf897-144">INPUTS</span></span>

## <span data-ttu-id="cf897-145">輸出</span><span class="sxs-lookup"><span data-stu-id="cf897-145">OUTPUTS</span></span>

## <span data-ttu-id="cf897-146">注意</span><span class="sxs-lookup"><span data-stu-id="cf897-146">NOTES</span></span>

## <span data-ttu-id="cf897-147">相關連結</span><span class="sxs-lookup"><span data-stu-id="cf897-147">RELATED LINKS</span></span>

[<span data-ttu-id="cf897-148">about_Providers</span><span class="sxs-lookup"><span data-stu-id="cf897-148">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="cf897-149">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="cf897-149">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="cf897-150">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="cf897-150">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
