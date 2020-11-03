---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 07/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 4bbdab62168a7306bb02d0ac47b5513d23920814
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205795"
---
# <span data-ttu-id="29d5b-103">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="29d5b-103">ConvertFrom-SecureString</span></span>

## <span data-ttu-id="29d5b-104">概要</span><span class="sxs-lookup"><span data-stu-id="29d5b-104">SYNOPSIS</span></span>
<span data-ttu-id="29d5b-105">將安全字串轉換成加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-105">Converts a secure string to an encrypted standard string.</span></span>

## <span data-ttu-id="29d5b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29d5b-106">SYNTAX</span></span>

### <span data-ttu-id="29d5b-107">Secure (預設值)</span><span class="sxs-lookup"><span data-stu-id="29d5b-107">Secure (Default)</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="29d5b-108">AsPlainText</span><span class="sxs-lookup"><span data-stu-id="29d5b-108">AsPlainText</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-AsPlainText] [<CommonParameters>]
```

### <span data-ttu-id="29d5b-109">開啟</span><span class="sxs-lookup"><span data-stu-id="29d5b-109">Open</span></span>

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="29d5b-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="29d5b-110">DESCRIPTION</span></span>

<span data-ttu-id="29d5b-111">**Convertfrom-string-SecureString** 指令程式會將安全字串 ( **SecureString** ) 轉換成加密標準字串， ( **system.string** ) 。</span><span class="sxs-lookup"><span data-stu-id="29d5b-111">The **ConvertFrom-SecureString** cmdlet converts a secure string ( **System.Security.SecureString** ) into an encrypted standard string ( **System.String** ).</span></span> <span data-ttu-id="29d5b-112">與安全字串不同，加密標準字串可以儲存在檔案中供日後使用。</span><span class="sxs-lookup"><span data-stu-id="29d5b-112">Unlike a secure string, an encrypted standard string can be saved in a file for later use.</span></span> <span data-ttu-id="29d5b-113">您可以使用 Cmdlet，將加密的標準字串轉換回其安全字串格式 `ConvertTo-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="29d5b-113">The encrypted standard string can be converted back to its secure string format by using the `ConvertTo-SecureString` cmdlet.</span></span>

<span data-ttu-id="29d5b-114">如果是使用 **Key** 或 **SecureKey** 參數來指定加密金鑰，便會使用「進階加密標準」(AES) 加密演算法。</span><span class="sxs-lookup"><span data-stu-id="29d5b-114">If an encryption key is specified by using the **Key** or **SecureKey** parameters, the Advanced Encryption Standard (AES) encryption algorithm is used.</span></span> <span data-ttu-id="29d5b-115">指定之金鑰的長度必須為 128、192 或 256 個位元，因為這些是 AES 加密演算法所支援的金鑰長度。</span><span class="sxs-lookup"><span data-stu-id="29d5b-115">The specified key must have a length of 128, 192, or 256 bits because those are the key lengths supported by the AES encryption algorithm.</span></span> <span data-ttu-id="29d5b-116">如果未指定任何金鑰，則會使用「Windows 資料保護 API」(DPAPI) 來加密標準字串表示法。</span><span class="sxs-lookup"><span data-stu-id="29d5b-116">If no key is specified, the Windows Data Protection API (DPAPI) is used to encrypt the standard string representation.</span></span>

> [!NOTE]
> <span data-ttu-id="29d5b-117">請注意，在非 Windows 系統上，每個 [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks)都不會加密 SecureString 的內容。</span><span class="sxs-lookup"><span data-stu-id="29d5b-117">Note that per [DotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks), the contents of a SecureString are not encrypted on non-Windows systems.</span></span>

## <span data-ttu-id="29d5b-118">範例</span><span class="sxs-lookup"><span data-stu-id="29d5b-118">EXAMPLES</span></span>

### <span data-ttu-id="29d5b-119">範例 1︰建立安全字串</span><span class="sxs-lookup"><span data-stu-id="29d5b-119">Example 1: Create a secure string</span></span>

```powershell
$SecureString = Read-Host -AsSecureString
```

<span data-ttu-id="29d5b-120">這個命令會從您在命令提示字元中輸入的字元建立安全字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-120">This command creates a secure string from characters that you type at the command prompt.</span></span> <span data-ttu-id="29d5b-121">輸入命令之後，請輸入您想要儲存為安全字串的字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-121">After entering the command, type the string you want to store as a secure string.</span></span> <span data-ttu-id="29d5b-122">`*`會顯示星號 () ，以代表您輸入的每個字元。</span><span class="sxs-lookup"><span data-stu-id="29d5b-122">An asterisk (`*`) is displayed to represent each character that you type.</span></span>

### <span data-ttu-id="29d5b-123">範例 2︰將安全字串轉換成加密標準字串</span><span class="sxs-lookup"><span data-stu-id="29d5b-123">Example 2: Convert a secure string to an encrypted standard string</span></span>

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

<span data-ttu-id="29d5b-124">此命令會將變數中的安全字串轉換 `$SecureString` 成加密的標準字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-124">This command converts the secure string in the `$SecureString` variable to an encrypted standard string.</span></span> <span data-ttu-id="29d5b-125">產生的加密標準字串會儲存在 `$StandardString` 變數中。</span><span class="sxs-lookup"><span data-stu-id="29d5b-125">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

### <span data-ttu-id="29d5b-126">範例 3︰將安全字串轉換成使用 192 位元金鑰的加密標準字串</span><span class="sxs-lookup"><span data-stu-id="29d5b-126">Example 3: Convert a secure string to an encrypted standard string with a 192-bit key</span></span>

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

<span data-ttu-id="29d5b-127">這些命令會使用進階加密標準 (AES) 演算法，將儲存在變數中的安全字串轉換成 `$SecureString` 具有192位金鑰的加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-127">These commands use the Advanced Encryption Standard (AES) algorithm to convert the secure string stored in the `$SecureString` variable to an encrypted standard string with a 192-bit key.</span></span> <span data-ttu-id="29d5b-128">產生的加密標準字串會儲存在 `$StandardString` 變數中。</span><span class="sxs-lookup"><span data-stu-id="29d5b-128">The resulting encrypted standard string is stored in the `$StandardString` variable.</span></span>

<span data-ttu-id="29d5b-129">第一個命令會將金鑰儲存在 `$Key` 變數中。</span><span class="sxs-lookup"><span data-stu-id="29d5b-129">The first command stores a key in the `$Key` variable.</span></span> <span data-ttu-id="29d5b-130">金鑰是24個十進位數的陣列，每個數位都必須小於256，才能納入單一不帶正負號的位元組內。</span><span class="sxs-lookup"><span data-stu-id="29d5b-130">The key is an array of 24 decimal numerals, each of which must be less than 256 to fit within a single unsigned byte.</span></span>

<span data-ttu-id="29d5b-131">因為每個十進位數都代表單一位元組 (8 個位) ，所以索引鍵有24位數，總共192位 (8 x 24) 。</span><span class="sxs-lookup"><span data-stu-id="29d5b-131">Because each decimal numeral represents a single byte (8 bits), the key has 24 digits for a total of 192 bits (8 x 24).</span></span> <span data-ttu-id="29d5b-132">這是 AES 演算法的有效金鑰長度。</span><span class="sxs-lookup"><span data-stu-id="29d5b-132">This is a valid key length for the AES algorithm.</span></span>

<span data-ttu-id="29d5b-133">第二個命令會使用變數中的索引鍵 `$Key` ，將安全字串轉換成加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-133">The second command uses the key in the `$Key` variable to convert the secure string to an encrypted standard string.</span></span>

### <span data-ttu-id="29d5b-134">範例4：將安全字串直接轉換為純文字字串</span><span class="sxs-lookup"><span data-stu-id="29d5b-134">Example 4: Convert a secure string directly to a plaintext string</span></span>

```powershell
$secureString = ConvertTo-SecureString -String 'Example' -AsPlainText
$secureString # 'System.Security.SecureString'
ConvertFrom-SecureString -SecureString $secureString -AsPlainText # 'Example'
```

## <span data-ttu-id="29d5b-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29d5b-135">PARAMETERS</span></span>

### <span data-ttu-id="29d5b-136">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="29d5b-136">-AsPlainText</span></span>

<span data-ttu-id="29d5b-137">設定時， `ConvertFrom-SecureString` 會將安全字串轉換成解密的純文字字串作為輸出。</span><span class="sxs-lookup"><span data-stu-id="29d5b-137">When set, `ConvertFrom-SecureString` will convert secure strings to the decrypted plaintext string as output.</span></span>

<span data-ttu-id="29d5b-138">此辨識已新增至 PowerShell 7.0。</span><span class="sxs-lookup"><span data-stu-id="29d5b-138">This paramater was added in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsPlainText
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29d5b-139">-Key</span><span class="sxs-lookup"><span data-stu-id="29d5b-139">-Key</span></span>

<span data-ttu-id="29d5b-140">將加密金鑰指定為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="29d5b-140">Specifies the encryption key as a byte array.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29d5b-141">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="29d5b-141">-SecureKey</span></span>

<span data-ttu-id="29d5b-142">將加密金鑰指定為安全字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-142">Specifies the encryption key as a secure string.</span></span> <span data-ttu-id="29d5b-143">安全字串值在被當作金鑰使用之前，會先轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="29d5b-143">The secure string value is converted to a byte array before being used as the key.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29d5b-144">-SecureString</span><span class="sxs-lookup"><span data-stu-id="29d5b-144">-SecureString</span></span>

<span data-ttu-id="29d5b-145">指定要轉換成加密標準字串的安全字串。</span><span class="sxs-lookup"><span data-stu-id="29d5b-145">Specifies the secure string to convert to an encrypted standard string.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="29d5b-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29d5b-146">CommonParameters</span></span>

<span data-ttu-id="29d5b-147">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="29d5b-147">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`,`-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="29d5b-148">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="29d5b-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29d5b-149">輸入</span><span class="sxs-lookup"><span data-stu-id="29d5b-149">INPUTS</span></span>

### <span data-ttu-id="29d5b-150">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="29d5b-150">System.Security.SecureString</span></span>

<span data-ttu-id="29d5b-151">您可以使用管線將 **SecureString** 物件傳送至 Convertfrom-string-SecureString。</span><span class="sxs-lookup"><span data-stu-id="29d5b-151">You can pipe a **SecureString** object to ConvertFrom-SecureString.</span></span>

## <span data-ttu-id="29d5b-152">輸出</span><span class="sxs-lookup"><span data-stu-id="29d5b-152">OUTPUTS</span></span>

### <span data-ttu-id="29d5b-153">System.String</span><span class="sxs-lookup"><span data-stu-id="29d5b-153">System.String</span></span>

<span data-ttu-id="29d5b-154">ConvertFrom-SecureString 會傳回標準字串物件。</span><span class="sxs-lookup"><span data-stu-id="29d5b-154">ConvertFrom-SecureString returns a standard string object.</span></span>

## <span data-ttu-id="29d5b-155">注意</span><span class="sxs-lookup"><span data-stu-id="29d5b-155">NOTES</span></span>

- <span data-ttu-id="29d5b-156">若要從命令提示字元輸入的字元建立安全字串，請使用 Cmdlet 的 **AsSecureString** 參數 `Read-Host` 。</span><span class="sxs-lookup"><span data-stu-id="29d5b-156">To create a secure string from characters that are typed at the command prompt, use the **AsSecureString** parameter of the `Read-Host` cmdlet.</span></span>
- <span data-ttu-id="29d5b-157">當您使用 **key** 或 **SecureKey** 參數來指定金鑰時，金鑰長度必須正確。</span><span class="sxs-lookup"><span data-stu-id="29d5b-157">When you use the **Key** or **SecureKey** parameters to specify a key, the key length must be correct.</span></span> <span data-ttu-id="29d5b-158">例如，可以將128位的索引鍵指定為16個小數位數的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="29d5b-158">For example, a key of 128 bits can be specified as a byte array of 16 decimal numerals.</span></span>
  <span data-ttu-id="29d5b-159">同樣地，192位和256位的金鑰會分別對應至24和32十進位數的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="29d5b-159">Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 decimal numerals, respectively.</span></span>
- <span data-ttu-id="29d5b-160">某些字元（例如圖釋）會對應至包含它們的字串中的數個程式碼點。</span><span class="sxs-lookup"><span data-stu-id="29d5b-160">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="29d5b-161">請避免使用這些字元，因為它們在密碼中使用時可能會造成問題和誤解。</span><span class="sxs-lookup"><span data-stu-id="29d5b-161">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="29d5b-162">相關連結</span><span class="sxs-lookup"><span data-stu-id="29d5b-162">RELATED LINKS</span></span>

[<span data-ttu-id="29d5b-163">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="29d5b-163">ConvertTo-SecureString</span></span>](ConvertTo-SecureString.md)

[<span data-ttu-id="29d5b-164">Read-Host</span><span class="sxs-lookup"><span data-stu-id="29d5b-164">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
