---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 3c82d1342f5e16da0b1bb0307bc0f5ff31b4828c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202831"
---
# <span data-ttu-id="b86e5-103">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="b86e5-103">Get-FileHash</span></span>

## <span data-ttu-id="b86e5-104">概要</span><span class="sxs-lookup"><span data-stu-id="b86e5-104">SYNOPSIS</span></span>
<span data-ttu-id="b86e5-105">使用指定的雜湊演算法來計算檔案的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-105">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="b86e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b86e5-106">SYNTAX</span></span>

### <span data-ttu-id="b86e5-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="b86e5-107">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="b86e5-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b86e5-108">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="b86e5-109">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="b86e5-109">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="b86e5-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b86e5-110">DESCRIPTION</span></span>

<span data-ttu-id="b86e5-111">此 `Get-FileHash` Cmdlet 會使用指定的雜湊演算法來計算檔案的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-111">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="b86e5-112">雜湊值是對應至檔案內容的唯一值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-112">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="b86e5-113">雜湊會指派唯一值至檔案內容，而非依檔案名稱、副檔名或其他指定項目來識別檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="b86e5-113">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="b86e5-114">您可以在不修改檔案內容的情況下變更檔案名稱與副檔名，這樣不會變更雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-114">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="b86e5-115">同樣地，檔案的內容可以變更，而不需要變更名稱或副檔名。</span><span class="sxs-lookup"><span data-stu-id="b86e5-115">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="b86e5-116">不過，即使只變更檔案內容中的一個字元，也會造成檔案的雜湊值變更。</span><span class="sxs-lookup"><span data-stu-id="b86e5-116">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="b86e5-117">雜湊值的目的是提供以密碼編譯的安全方式來確認檔案內容未經變更。</span><span class="sxs-lookup"><span data-stu-id="b86e5-117">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="b86e5-118">雖然某些雜湊演算法（包括 MD5 和 SHA1）不再被視為安全的攻擊，但是安全雜湊演算法的目標是要將它轉譯為不可能變更檔案的內容，不論是不小心，或是惡意或未經授權的嘗試，並維持相同的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-118">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="b86e5-119">您也可以使用雜湊值來判斷兩個檔案是否具有完全相同的內容。</span><span class="sxs-lookup"><span data-stu-id="b86e5-119">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="b86e5-120">若兩個檔案的雜湊值完全相同，則檔案的內容也完全相同。</span><span class="sxs-lookup"><span data-stu-id="b86e5-120">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="b86e5-121">根據預設，此 `Get-FileHash` Cmdlet 會使用 SHA256 演算法，雖然可以使用目標作業系統所支援的任何雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="b86e5-121">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="b86e5-122">範例</span><span class="sxs-lookup"><span data-stu-id="b86e5-122">EXAMPLES</span></span>

### <span data-ttu-id="b86e5-123">範例1：計算檔案的雜湊值</span><span class="sxs-lookup"><span data-stu-id="b86e5-123">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="b86e5-124">此範例會使用 `Get-FileHash` Cmdlet 來計算檔案的雜湊值 `/etc/apt/sources.list` 。</span><span class="sxs-lookup"><span data-stu-id="b86e5-124">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="b86e5-125">使用的雜湊演算法是預設的 **SHA256** 。</span><span class="sxs-lookup"><span data-stu-id="b86e5-125">The hash algorithm used is the default, **SHA256** .</span></span> <span data-ttu-id="b86e5-126">輸出會透過管道傳送至 `Format-List` Cmdlet，以將輸出格式化為清單。</span><span class="sxs-lookup"><span data-stu-id="b86e5-126">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="b86e5-127">範例2：計算 ISO 檔案的雜湊值</span><span class="sxs-lookup"><span data-stu-id="b86e5-127">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="b86e5-128">此範例會使用 `Get-FileHash` Cmdlet 和 **SHA384** 演算法來計算系統管理員已從網際網路下載的 ISO 檔案的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-128">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="b86e5-129">輸出會透過管道傳送至 `Format-List` Cmdlet，以將輸出格式化為清單。</span><span class="sxs-lookup"><span data-stu-id="b86e5-129">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="b86e5-130">範例3：計算資料流程的雜湊值</span><span class="sxs-lookup"><span data-stu-id="b86e5-130">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="b86e5-131">在此範例中，我們會使用 **系統 .net** ，從 [Powershell 版本頁面](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)下載套件。</span><span class="sxs-lookup"><span data-stu-id="b86e5-131">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="b86e5-132">[發行] 頁面也會記錄每個封裝檔案的 SHA256 雜湊。</span><span class="sxs-lookup"><span data-stu-id="b86e5-132">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="b86e5-133">我們可以將已發佈的雜湊值與我們用來計算的雜湊值進行比較 `Get-FileHash` 。</span><span class="sxs-lookup"><span data-stu-id="b86e5-133">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### <span data-ttu-id="b86e5-134">範例4：計算字串的雜湊</span><span class="sxs-lookup"><span data-stu-id="b86e5-134">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="b86e5-135">PowerShell 不會提供 Cmdlet 來計算字串的雜湊。</span><span class="sxs-lookup"><span data-stu-id="b86e5-135">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="b86e5-136">不過，您可以將字串寫入資料流程，並使用的 **InputStream** 參數 `Get-FileHash` 來取得雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-136">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## <span data-ttu-id="b86e5-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b86e5-137">PARAMETERS</span></span>

### <span data-ttu-id="b86e5-138">-演算法</span><span class="sxs-lookup"><span data-stu-id="b86e5-138">-Algorithm</span></span>

<span data-ttu-id="b86e5-139">指定密碼編譯雜湊函式，用來計算指定檔案或資料流程內容的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-139">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="b86e5-140">密碼編譯雜湊函式具有屬性，因此找不到具有相同雜湊值的兩個不同檔案。</span><span class="sxs-lookup"><span data-stu-id="b86e5-140">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="b86e5-141">雜湊函式經常被用於數位簽章與資料完整性用途。</span><span class="sxs-lookup"><span data-stu-id="b86e5-141">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="b86e5-142">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="b86e5-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b86e5-143">SHA1</span><span class="sxs-lookup"><span data-stu-id="b86e5-143">SHA1</span></span>
- <span data-ttu-id="b86e5-144">SHA256</span><span class="sxs-lookup"><span data-stu-id="b86e5-144">SHA256</span></span>
- <span data-ttu-id="b86e5-145">SHA384</span><span class="sxs-lookup"><span data-stu-id="b86e5-145">SHA384</span></span>
- <span data-ttu-id="b86e5-146">SHA512</span><span class="sxs-lookup"><span data-stu-id="b86e5-146">SHA512</span></span>
- <span data-ttu-id="b86e5-147">MD5</span><span class="sxs-lookup"><span data-stu-id="b86e5-147">MD5</span></span>

<span data-ttu-id="b86e5-148">若未指定值，或省略參數，則預設值是 SHA256。</span><span class="sxs-lookup"><span data-stu-id="b86e5-148">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="b86e5-149">基於安全性理由，MD5 與 SHA1 (不再被視為安全) 只應該用於簡單的變更驗證，而不應該用於為需要保護以避免受攻擊或遭竄改的檔案產生雜湊值。</span><span class="sxs-lookup"><span data-stu-id="b86e5-149">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b86e5-150">-InputStream</span><span class="sxs-lookup"><span data-stu-id="b86e5-150">-InputStream</span></span>

<span data-ttu-id="b86e5-151">指定輸入資料流程。</span><span class="sxs-lookup"><span data-stu-id="b86e5-151">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b86e5-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b86e5-152">-LiteralPath</span></span>

<span data-ttu-id="b86e5-153">指定檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="b86e5-153">Specifies the path to a file.</span></span> <span data-ttu-id="b86e5-154">與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="b86e5-154">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b86e5-155">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b86e5-155">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b86e5-156">如果路徑包含逸出字元，請將路徑括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="b86e5-156">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="b86e5-157">單引號指示 PowerShell 不要將字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="b86e5-157">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b86e5-158">-Path</span><span class="sxs-lookup"><span data-stu-id="b86e5-158">-Path</span></span>

<span data-ttu-id="b86e5-159">指定一或多個檔案的路徑做為陣列。</span><span class="sxs-lookup"><span data-stu-id="b86e5-159">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="b86e5-160">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b86e5-160">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="b86e5-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b86e5-161">CommonParameters</span></span>

<span data-ttu-id="b86e5-162">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b86e5-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b86e5-163">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b86e5-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b86e5-164">輸入</span><span class="sxs-lookup"><span data-stu-id="b86e5-164">INPUTS</span></span>

### <span data-ttu-id="b86e5-165">System.String</span><span class="sxs-lookup"><span data-stu-id="b86e5-165">System.String</span></span>

<span data-ttu-id="b86e5-166">您可以使用管線將字串傳送至 `Get-FileHash` Cmdlet，其中包含一個或多個檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="b86e5-166">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="b86e5-167">輸出</span><span class="sxs-lookup"><span data-stu-id="b86e5-167">OUTPUTS</span></span>

### <span data-ttu-id="b86e5-168">Get-filehash。</span><span class="sxs-lookup"><span data-stu-id="b86e5-168">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="b86e5-169">`Get-FileHash` 傳回物件，這個物件表示指定檔案的路徑、計算的雜湊值，以及用來計算雜湊的演算法。</span><span class="sxs-lookup"><span data-stu-id="b86e5-169">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="b86e5-170">注意</span><span class="sxs-lookup"><span data-stu-id="b86e5-170">NOTES</span></span>

## <span data-ttu-id="b86e5-171">相關連結</span><span class="sxs-lookup"><span data-stu-id="b86e5-171">RELATED LINKS</span></span>

[<span data-ttu-id="b86e5-172">Format-List</span><span class="sxs-lookup"><span data-stu-id="b86e5-172">Format-List</span></span>](Format-List.md)

