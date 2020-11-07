---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: 66ecd756eccbe60003304419da64d65b6c55dd01
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347732"
---
# <span data-ttu-id="20974-103">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="20974-103">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="20974-104">概要</span><span class="sxs-lookup"><span data-stu-id="20974-104">SYNOPSIS</span></span>
<span data-ttu-id="20974-105">將 [Authenticode](/windows-hardware/drivers/install/authenticode) 簽章新增至 PowerShell 腳本或其他檔案。</span><span class="sxs-lookup"><span data-stu-id="20974-105">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="20974-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20974-106">SYNTAX</span></span>

### <span data-ttu-id="20974-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="20974-107">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20974-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="20974-108">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20974-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="20974-109">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="20974-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="20974-110">DESCRIPTION</span></span>

<span data-ttu-id="20974-111">`Set-AuthenticodeSignature`Cmdlet 會將 Authenticode 簽章新增至任何支援主體介面套件 (SIP) 的檔案。</span><span class="sxs-lookup"><span data-stu-id="20974-111">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="20974-112">在 PowerShell 腳本檔案中，簽章會採用文字區塊的形式，指出腳本中執行的指示結尾。</span><span class="sxs-lookup"><span data-stu-id="20974-112">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="20974-113">如果執行此 Cmdlet 時檔案中有簽章，會移除該簽章。</span><span class="sxs-lookup"><span data-stu-id="20974-113">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="20974-114">範例</span><span class="sxs-lookup"><span data-stu-id="20974-114">EXAMPLES</span></span>

### <span data-ttu-id="20974-115">範例 1-使用本機憑證存放區中的憑證簽署腳本</span><span class="sxs-lookup"><span data-stu-id="20974-115">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="20974-116">這些命令會從 PowerShell 憑證提供者取得程式碼簽署憑證，並使用它來簽署 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="20974-116">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="20974-117">第一個命令會使用 `Get-ChildItem` Cmdlet 和 PowerShell 憑證提供者取得 `Cert:\CurrentUser\My` 憑證存放區之子目錄中的憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-117">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="20974-118">`Cert:`磁片磁碟機是憑證提供者所公開的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="20974-118">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="20974-119">只有憑證提供者支援的 **CodeSigningCert** 參數，會將抓取的憑證限制為具有程式碼簽署授權單位的憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-119">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="20974-120">命令會將結果儲存在 `$cert` 變數中。</span><span class="sxs-lookup"><span data-stu-id="20974-120">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="20974-121">第二個命令會使用 `Set-AuthenticodeSignature` Cmdlet 來簽署 `PSTestInternet2.ps1` 腳本。</span><span class="sxs-lookup"><span data-stu-id="20974-121">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="20974-122">它會使用 **FilePath** 參數指定腳本的名稱，以及使用 **certificate** 參數指定憑證儲存在 `$cert` 變數中。</span><span class="sxs-lookup"><span data-stu-id="20974-122">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="20974-123">使用 **CodeSigningCert** 參數 `Get-ChildItem` 只會傳回具有程式碼簽署授權單位且包含私密金鑰的憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-123">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="20974-124">如果沒有私密金鑰，則憑證無法用於簽署。</span><span class="sxs-lookup"><span data-stu-id="20974-124">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="20974-125">範例 2-使用 PFX 檔案中的憑證簽署腳本</span><span class="sxs-lookup"><span data-stu-id="20974-125">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="20974-126">這些命令會使用 `Get-PfxCertificate` Cmdlet 載入程式碼簽署憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-126">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="20974-127">然後，使用它來簽署 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="20974-127">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="20974-128">第一個命令會使用 `Get-PfxCertificate` Cmdlet 將 C:\Test\MySign.pfx 憑證載入到變數中 `$cert` 。</span><span class="sxs-lookup"><span data-stu-id="20974-128">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="20974-129">第二個命令會使用 `Set-AuthenticodeSignature` 來簽署腳本。</span><span class="sxs-lookup"><span data-stu-id="20974-129">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="20974-130">的 **FilePath** 參數 `Set-AuthenticodeSignature` 指定要簽署的腳本檔案的路徑，而 **Cert** 參數則會將 `$cert` 包含憑證的變數傳遞給 `Set-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="20974-130">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="20974-131">如果憑證檔案有密碼保護，則 PowerShell 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="20974-131">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="20974-132">範例 3-新增包含根授權單位的簽章</span><span class="sxs-lookup"><span data-stu-id="20974-132">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="20974-133">此命令在信任鏈結中加入包含根授權單位的數位簽章，並由協力廠商的時間戳記伺服器進行簽署。</span><span class="sxs-lookup"><span data-stu-id="20974-133">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="20974-134">此命令會使用 **FilePath** 參數指定要簽署的腳本，以及使用 **certificate** 參數指定儲存在變數中的憑證 `$cert` 。</span><span class="sxs-lookup"><span data-stu-id="20974-134">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="20974-135">它使用 **IncludeChain** 參數來包含信任鏈中的所有簽章，包括根授權單位。</span><span class="sxs-lookup"><span data-stu-id="20974-135">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="20974-136">它也會使用 **TimeStampServer** 參數將時間戳記加入簽章。</span><span class="sxs-lookup"><span data-stu-id="20974-136">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="20974-137">這可防止指令碼在憑證過期時失敗。</span><span class="sxs-lookup"><span data-stu-id="20974-137">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="20974-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20974-138">PARAMETERS</span></span>

### <span data-ttu-id="20974-139">-Certificate</span><span class="sxs-lookup"><span data-stu-id="20974-139">-Certificate</span></span>

<span data-ttu-id="20974-140">指定要用來簽署指令碼或檔案的憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-140">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="20974-141">輸入儲存代表憑證之物件的變數，或取得憑證的運算式。</span><span class="sxs-lookup"><span data-stu-id="20974-141">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="20974-142">若要尋找憑證，請使用 `Get-PfxCertificate` 或使用 `Get-ChildItem` 憑證磁片磁碟機中的 Cmdlet `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="20974-142">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="20974-143">若憑證無效或沒有 `code-signing` 授權單位，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="20974-143">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-144">-FilePath</span><span class="sxs-lookup"><span data-stu-id="20974-144">-FilePath</span></span>

<span data-ttu-id="20974-145">指定要簽署的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="20974-145">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="20974-146">-Force</span><span class="sxs-lookup"><span data-stu-id="20974-146">-Force</span></span>

<span data-ttu-id="20974-147">可讓 Cmdlet 將簽章附加到唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="20974-147">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="20974-148">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="20974-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-149">-HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="20974-149">-HashAlgorithm</span></span>

<span data-ttu-id="20974-150">指定 Windows 用來計算檔案數位簽章的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="20974-150">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="20974-151">針對 PowerShell 3.0，預設值是 SHA256，這是 Windows 預設的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="20974-151">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="20974-152">針對 PowerShell 2.0，預設值為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="20974-152">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="20974-153">在其他系統上可能無法辨識以不同雜湊演算法所簽署的檔案。</span><span class="sxs-lookup"><span data-stu-id="20974-153">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="20974-154">支援哪些演算法取決於作業系統的版本。</span><span class="sxs-lookup"><span data-stu-id="20974-154">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="20974-155">如需可能值的清單，請參閱 [HashAlgorithmName 結構](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties)。</span><span class="sxs-lookup"><span data-stu-id="20974-155">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-156">-IncludeChain</span><span class="sxs-lookup"><span data-stu-id="20974-156">-IncludeChain</span></span>

<span data-ttu-id="20974-157">判斷數位簽章中包含憑證信任鏈結中的哪個憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-157">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="20974-158">預設值為 **NotRoot** 。</span><span class="sxs-lookup"><span data-stu-id="20974-158">**NotRoot** is the default.</span></span>

<span data-ttu-id="20974-159">有效值為：</span><span class="sxs-lookup"><span data-stu-id="20974-159">Valid values are:</span></span>

- <span data-ttu-id="20974-160">Signer：只包含簽署者的憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-160">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="20974-161">NotRoot：包含憑證鏈結中 (除了根授權單位) 的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-161">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="20974-162">全部：包含憑證鏈中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="20974-162">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-163">-TimestampServer</span><span class="sxs-lookup"><span data-stu-id="20974-163">-TimestampServer</span></span>

<span data-ttu-id="20974-164">使用指定的時間戳記伺服器將時間戳記加入簽章。</span><span class="sxs-lookup"><span data-stu-id="20974-164">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="20974-165">以字串方式輸入時間戳記伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="20974-165">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="20974-166">時間戳記代表憑證加入檔案的確切時間。</span><span class="sxs-lookup"><span data-stu-id="20974-166">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="20974-167">如果憑證過期，時間戳記會防止指令碼失敗，因為使用者和程式可以驗證憑證在簽署時是有效的。</span><span class="sxs-lookup"><span data-stu-id="20974-167">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-168">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="20974-168">-LiteralPath</span></span>

<span data-ttu-id="20974-169">指定要簽署的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="20974-169">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="20974-170">**LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="20974-170">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="20974-171">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="20974-171">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="20974-172">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="20974-172">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="20974-173">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="20974-173">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20974-174">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="20974-174">-SourcePathOrExtension</span></span>

<span data-ttu-id="20974-175">加入數位簽章之內容的檔案或檔案類型路徑。</span><span class="sxs-lookup"><span data-stu-id="20974-175">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="20974-176">此參數會搭配將檔案內容當做位元組陣列傳遞的 **內容** 使用。</span><span class="sxs-lookup"><span data-stu-id="20974-176">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="20974-177">-Content</span><span class="sxs-lookup"><span data-stu-id="20974-177">-Content</span></span>

<span data-ttu-id="20974-178">檔案的內容，做為加入數位簽章的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="20974-178">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="20974-179">此參數必須搭配 **SourcePathOrExtension** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="20974-179">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="20974-180">檔案內容的格式必須是 Unicode (UTF-16LE) 格式。</span><span class="sxs-lookup"><span data-stu-id="20974-180">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20974-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20974-181">-Confirm</span></span>

<span data-ttu-id="20974-182">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="20974-182">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20974-183">-WhatIf</span></span>

<span data-ttu-id="20974-184">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="20974-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="20974-185">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="20974-185">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20974-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20974-186">CommonParameters</span></span>

<span data-ttu-id="20974-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="20974-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20974-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="20974-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20974-189">輸入</span><span class="sxs-lookup"><span data-stu-id="20974-189">INPUTS</span></span>

### <span data-ttu-id="20974-190">System.String</span><span class="sxs-lookup"><span data-stu-id="20974-190">System.String</span></span>

<span data-ttu-id="20974-191">您可以使用管線將包含檔案路徑的字串傳送至 `Set-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="20974-191">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="20974-192">輸出</span><span class="sxs-lookup"><span data-stu-id="20974-192">OUTPUTS</span></span>

### <span data-ttu-id="20974-193">System.Management.Automation.Signature</span><span class="sxs-lookup"><span data-stu-id="20974-193">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="20974-194">注意</span><span class="sxs-lookup"><span data-stu-id="20974-194">NOTES</span></span>

<span data-ttu-id="20974-195">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="20974-195">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="20974-196">相關連結</span><span class="sxs-lookup"><span data-stu-id="20974-196">RELATED LINKS</span></span>

[<span data-ttu-id="20974-197">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="20974-197">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="20974-198">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="20974-198">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="20974-199">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="20974-199">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="20974-200">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="20974-200">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="20974-201">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="20974-201">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="20974-202">about_Signing</span><span class="sxs-lookup"><span data-stu-id="20974-202">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
