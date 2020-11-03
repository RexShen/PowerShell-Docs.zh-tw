---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 6e536681f78a79660e80951d0dcc446fbba32553
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "93208860"
---
# <span data-ttu-id="477b2-103">ConvertTo-SecureString</span><span class="sxs-lookup"><span data-stu-id="477b2-103">ConvertTo-SecureString</span></span>

## <span data-ttu-id="477b2-104">概要</span><span class="sxs-lookup"><span data-stu-id="477b2-104">SYNOPSIS</span></span>
<span data-ttu-id="477b2-105">將純文字或加密字串轉換成安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-105">Converts plain text or encrypted strings to secure strings.</span></span>

## <span data-ttu-id="477b2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="477b2-106">SYNTAX</span></span>

### <span data-ttu-id="477b2-107">Secure (預設值)</span><span class="sxs-lookup"><span data-stu-id="477b2-107">Secure (Default)</span></span>

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### <span data-ttu-id="477b2-108">PlainText</span><span class="sxs-lookup"><span data-stu-id="477b2-108">PlainText</span></span>

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="477b2-109">開啟</span><span class="sxs-lookup"><span data-stu-id="477b2-109">Open</span></span>

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## <span data-ttu-id="477b2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="477b2-110">DESCRIPTION</span></span>

<span data-ttu-id="477b2-111">此 `ConvertTo-SecureString` Cmdlet 會將加密的標準字串轉換成安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-111">The `ConvertTo-SecureString` cmdlet converts encrypted standard strings into secure strings.</span></span> <span data-ttu-id="477b2-112">它也可以將純文字轉換成安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-112">It can also convert plain text to secure strings.</span></span> <span data-ttu-id="477b2-113">它會搭配 `ConvertFrom-SecureString` 和使用 `Read-Host` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-113">It is used with `ConvertFrom-SecureString` and `Read-Host`.</span></span> <span data-ttu-id="477b2-114">Cmdlet 所建立的安全字串可搭配需要 **SecureString** 類型之參數的 Cmdlet 或函式使用。</span><span class="sxs-lookup"><span data-stu-id="477b2-114">The secure string created by the cmdlet can be used with cmdlets or functions that require a parameter of type **SecureString**.</span></span> <span data-ttu-id="477b2-115">您可以使用 Cmdlet，將安全字串轉換回加密的標準字串 `ConvertFrom-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-115">The secure string can be converted back to an encrypted, standard string using the `ConvertFrom-SecureString` cmdlet.</span></span> <span data-ttu-id="477b2-116">這可讓它儲存在檔案中以供日後使用。</span><span class="sxs-lookup"><span data-stu-id="477b2-116">This enables it to be stored in a file for later use.</span></span>

<span data-ttu-id="477b2-117">如果要轉換的標準字串使用 `ConvertFrom-SecureString` 指定的金鑰進行加密，則必須提供該相同的金鑰作為 Cmdlet 的 **Key** 或 **SecureKey** 參數值 `ConvertTo-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-117">If the standard string being converted was encrypted with `ConvertFrom-SecureString` using a specified key, that same key must be provided as the value of the **Key** or **SecureKey** parameter of the `ConvertTo-SecureString` cmdlet.</span></span>

## <span data-ttu-id="477b2-118">範例</span><span class="sxs-lookup"><span data-stu-id="477b2-118">EXAMPLES</span></span>

### <span data-ttu-id="477b2-119">範例1：將安全字串轉換成加密字串</span><span class="sxs-lookup"><span data-stu-id="477b2-119">Example 1: Convert a secure string to an encrypted string</span></span>

<span data-ttu-id="477b2-120">此範例顯示如何從使用者輸入建立安全字串、將安全字串轉換成加密的標準字串，然後再將加密的標準字串轉換回安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-120">This example shows how to create a secure string from user input, convert the secure string to an encrypted standard string, and then convert the encrypted standard string back to a secure string.</span></span>

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

<span data-ttu-id="477b2-121">第一個命令會使用 Cmdlet 的 **AsSecureString** 參數 `Read-Host` 來建立安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-121">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="477b2-122">輸入命令之後，您輸入的任何字元都會轉換成安全字串，然後儲存在 `$Secure` 變數中。</span><span class="sxs-lookup"><span data-stu-id="477b2-122">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="477b2-123">第二個命令會顯示變數的內容 `$Secure` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-123">The second command displays the contents of the `$Secure` variable.</span></span> <span data-ttu-id="477b2-124">因為 `$Secure` 變數包含安全字串，所以 PowerShell 只會顯示 **SecureString** 類型。</span><span class="sxs-lookup"><span data-stu-id="477b2-124">Because the `$Secure` variable contains a secure string, PowerShell displays only the **System.Security.SecureString** type.</span></span>

<span data-ttu-id="477b2-125">第三個命令會使用 `ConvertFrom-SecureString` Cmdlet 將變數中的安全字串轉換 `$Secure` 成加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-125">The third command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string.</span></span> <span data-ttu-id="477b2-126">它會將結果儲存在 `$Encrypted` 變數中。</span><span class="sxs-lookup"><span data-stu-id="477b2-126">It saves the result in the `$Encrypted` variable.</span></span>

<span data-ttu-id="477b2-127">第四個命令會在變數的值中顯示加密字串 `$Encrypted` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-127">The fourth command displays the encrypted string in the value of the `$Encrypted` variable.</span></span>

<span data-ttu-id="477b2-128">第五個命令會使用 `ConvertTo-SecureString` Cmdlet 將變數中的加密標準字串轉換 `$Encrypted` 回安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-128">The fifth command uses the `ConvertTo-SecureString` cmdlet to convert the encrypted standard string in the `$Encrypted` variable back into a secure string.</span></span> <span data-ttu-id="477b2-129">它會將結果儲存在 `$Secure2` 變數中。</span><span class="sxs-lookup"><span data-stu-id="477b2-129">It saves the result in the `$Secure2` variable.</span></span>
<span data-ttu-id="477b2-130">第六個命令會顯示變數的值 `$Secure2` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-130">The sixth command displays the value of the `$Secure2` variable.</span></span> <span data-ttu-id="477b2-131">SecureString 類型表示命令已成功。</span><span class="sxs-lookup"><span data-stu-id="477b2-131">The SecureString type indicates that the command was successful.</span></span>

### <span data-ttu-id="477b2-132">範例2：從檔案中的加密字串建立安全字串</span><span class="sxs-lookup"><span data-stu-id="477b2-132">Example 2: Create a secure string from an encrypted string in a file</span></span>

<span data-ttu-id="477b2-133">此範例顯示如何從儲存在檔案中之加密標準字串建立安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-133">This example shows how to create a secure string from an encrypted standard string that is saved in a file.</span></span>

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

<span data-ttu-id="477b2-134">第一個命令會使用 Cmdlet 的 **AsSecureString** 參數 `Read-Host` 來建立安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-134">The first command uses the **AsSecureString** parameter of the `Read-Host` cmdlet to create a secure string.</span></span> <span data-ttu-id="477b2-135">輸入命令之後，您輸入的任何字元都會轉換成安全字串，然後儲存在 `$Secure` 變數中。</span><span class="sxs-lookup"><span data-stu-id="477b2-135">After you enter the command, any characters that you type are converted into a secure string and then saved in the `$Secure` variable.</span></span>

<span data-ttu-id="477b2-136">第二個命令會使用 `ConvertFrom-SecureString` Cmdlet 將變數中的安全字串轉換 `$Secure` 成加密的標準字串，方法是使用指定的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="477b2-136">The second command uses the `ConvertFrom-SecureString` cmdlet to convert the secure string in the `$Secure` variable into an encrypted standard string by using the specified key.</span></span> <span data-ttu-id="477b2-137">內容會儲存在變數中 `$Encrypted` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-137">The contents are saved in the `$Encrypted` variable.</span></span>

<span data-ttu-id="477b2-138">第三個命令會使用管線運算子 (`|`) 將變數的值傳送 `$Encrypted` 至 `Set-Content` Cmdlet，以將值儲存在 Encrypted.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="477b2-138">The third command uses a pipeline operator (`|`) to send the value of the `$Encrypted` variable to the `Set-Content` cmdlet, which saves the value in the Encrypted.txt file.</span></span>

<span data-ttu-id="477b2-139">第四個命令會使用 `Get-Content` Cmdlet 取得 Encrypted.txt 檔案中的加密標準字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-139">The fourth command uses the `Get-Content` cmdlet to get the encrypted standard string in the Encrypted.txt file.</span></span> <span data-ttu-id="477b2-140">此命令會使用管線運算子將加密的字串傳送至 `ConvertTo-SecureString` Cmdlet，此 Cmdlet 會使用指定的金鑰將它轉換為安全字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-140">The command uses a pipeline operator to send the encrypted string to the `ConvertTo-SecureString` cmdlet, which converts it to a secure string by using the specified key.</span></span>
<span data-ttu-id="477b2-141">結果會儲存在變數中 `$Secure2` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-141">The results are saved in the `$Secure2` variable.</span></span>

### <span data-ttu-id="477b2-142">範例3：將純文字字串轉換成安全字串</span><span class="sxs-lookup"><span data-stu-id="477b2-142">Example 3: Convert a plain text string to a secure string</span></span>

<span data-ttu-id="477b2-143">此命令會將純文字字串轉換 `P@ssW0rD!` 成安全字串，並將結果儲存在 `$Secure_String_Pwd` 變數中。</span><span class="sxs-lookup"><span data-stu-id="477b2-143">This command converts the plain text string `P@ssW0rD!` into a secure string and stores the result in the `$Secure_String_Pwd` variable.</span></span> <span data-ttu-id="477b2-144">若要使用 **AsPlainText** 參數， **Force** 參數也必須包含在命令中。</span><span class="sxs-lookup"><span data-stu-id="477b2-144">To use the **AsPlainText** parameter, the **Force** parameter must also be included in the command.</span></span>

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> <span data-ttu-id="477b2-145">您應該避免在腳本中或從命令列使用純文字字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-145">You should avoid using plain text strings in script or from the command line.</span></span> <span data-ttu-id="477b2-146">純文字可能會顯示在事件記錄檔和命令歷程記錄中。</span><span class="sxs-lookup"><span data-stu-id="477b2-146">The plain text can show up in event logs and command history logs.</span></span>

## <span data-ttu-id="477b2-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="477b2-147">PARAMETERS</span></span>

### <span data-ttu-id="477b2-148">-AsPlainText</span><span class="sxs-lookup"><span data-stu-id="477b2-148">-AsPlainText</span></span>

<span data-ttu-id="477b2-149">指定要轉換成安全字串的純文字字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-149">Specifies a plain text string to convert to a secure string.</span></span> <span data-ttu-id="477b2-150">安全字串 Cmdlet 有助於保護機密文字。</span><span class="sxs-lookup"><span data-stu-id="477b2-150">The secure string cmdlets help protect confidential text.</span></span> <span data-ttu-id="477b2-151">為保有隱私，文字會加密，而且在使用後會從電腦記憶體中刪除。</span><span class="sxs-lookup"><span data-stu-id="477b2-151">The text is encrypted for privacy and is deleted from computer memory after it is used.</span></span> <span data-ttu-id="477b2-152">如果您使用此參數提供純文字做為輸入，系統就無法以此種方式保護保護該輸入。</span><span class="sxs-lookup"><span data-stu-id="477b2-152">If you use this parameter to provide plain text as input, the system cannot protect that input in this manner.</span></span> <span data-ttu-id="477b2-153">若要使用此參數，您也必須指定 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="477b2-153">To use this parameter, you must also specify the **Force** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="477b2-154">-Force</span><span class="sxs-lookup"><span data-stu-id="477b2-154">-Force</span></span>

<span data-ttu-id="477b2-155">確認您瞭解使用 **AsPlainText** 參數的含意，並仍想使用它。</span><span class="sxs-lookup"><span data-stu-id="477b2-155">Confirms that you understand the implications of using the **AsPlainText** parameter and still want to use it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="477b2-156">-Key</span><span class="sxs-lookup"><span data-stu-id="477b2-156">-Key</span></span>

<span data-ttu-id="477b2-157">指定用來將原始安全字串轉換成加密標準字串的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="477b2-157">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="477b2-158">有效的金鑰長度為16、24和32個位元組。</span><span class="sxs-lookup"><span data-stu-id="477b2-158">Valid key lengths are 16, 24 and 32 bytes.</span></span>

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

### <span data-ttu-id="477b2-159">-SecureKey</span><span class="sxs-lookup"><span data-stu-id="477b2-159">-SecureKey</span></span>

<span data-ttu-id="477b2-160">指定用來將原始安全字串轉換成加密標準字串的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="477b2-160">Specifies the encryption key used to convert the original secure string into the encrypted standard string.</span></span> <span data-ttu-id="477b2-161">金鑰需以安全字串的格式提供。</span><span class="sxs-lookup"><span data-stu-id="477b2-161">The key must be provided in the format of a secure string.</span></span> <span data-ttu-id="477b2-162">安全字串將會轉換成要當做金鑰使用的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="477b2-162">The secure string will be converted to a byte array to be used as the key.</span></span> <span data-ttu-id="477b2-163">有效的安全金鑰長度為8、12和16個程式碼點。</span><span class="sxs-lookup"><span data-stu-id="477b2-163">Valid secure key lengths are 8, 12 and 16 code points.</span></span>

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

### <span data-ttu-id="477b2-164">-String</span><span class="sxs-lookup"><span data-stu-id="477b2-164">-String</span></span>

<span data-ttu-id="477b2-165">指定要轉換成安全字串的字串。</span><span class="sxs-lookup"><span data-stu-id="477b2-165">Specifies the string to convert to a secure string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="477b2-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="477b2-166">CommonParameters</span></span>

<span data-ttu-id="477b2-167">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="477b2-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="477b2-168">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="477b2-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="477b2-169">輸入</span><span class="sxs-lookup"><span data-stu-id="477b2-169">INPUTS</span></span>

### <span data-ttu-id="477b2-170">System.String</span><span class="sxs-lookup"><span data-stu-id="477b2-170">System.String</span></span>

<span data-ttu-id="477b2-171">您可以使用管線將標準加密字串傳送至 `ConvertTo-SecureString` 。</span><span class="sxs-lookup"><span data-stu-id="477b2-171">You can pipe a standard encrypted string to `ConvertTo-SecureString`.</span></span>

## <span data-ttu-id="477b2-172">輸出</span><span class="sxs-lookup"><span data-stu-id="477b2-172">OUTPUTS</span></span>

### <span data-ttu-id="477b2-173">System.Security.SecureString</span><span class="sxs-lookup"><span data-stu-id="477b2-173">System.Security.SecureString</span></span>

<span data-ttu-id="477b2-174">`ConvertTo-SecureString` 傳回 **SecureString** 物件。</span><span class="sxs-lookup"><span data-stu-id="477b2-174">`ConvertTo-SecureString` returns a **SecureString** object.</span></span>

## <span data-ttu-id="477b2-175">注意</span><span class="sxs-lookup"><span data-stu-id="477b2-175">NOTES</span></span>

<span data-ttu-id="477b2-176">某些字元（例如圖釋）會對應至包含它們的字串中的數個程式碼點。</span><span class="sxs-lookup"><span data-stu-id="477b2-176">Some characters, such as emoticons, correspond to several code points in the string that contains them.</span></span> <span data-ttu-id="477b2-177">請避免使用這些字元，因為它們在密碼中使用時可能會造成問題和誤解。</span><span class="sxs-lookup"><span data-stu-id="477b2-177">Avoid using these characters because they may cause problems and misunderstandings when used in a password.</span></span>

## <span data-ttu-id="477b2-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="477b2-178">RELATED LINKS</span></span>

[<span data-ttu-id="477b2-179">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="477b2-179">ConvertFrom-SecureString</span></span>](ConvertFrom-SecureString.md)

[<span data-ttu-id="477b2-180">Read-Host</span><span class="sxs-lookup"><span data-stu-id="477b2-180">Read-Host</span></span>](../Microsoft.PowerShell.Utility/Read-Host.md)
