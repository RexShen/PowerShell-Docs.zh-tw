---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 新增與更新的 Cmdlet
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147588"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="85ff9-103">新增與更新的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="85ff9-103">New and updated cmdlets</span></span>

<span data-ttu-id="85ff9-104">我們根據社群的意見反應新增了新的 Cmdlet 並更新了現有的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="85ff9-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="85ff9-105">封存 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="85ff9-105">Archive cmdlets</span></span>

<span data-ttu-id="85ff9-106">兩個新的 Cmdlet `Compress-Archive` 和 `Expand-Archive` 可讓您壓縮和解壓縮 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="85ff9-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="85ff9-107">如需詳細資訊，請參閱 [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) 模組文件。</span><span class="sxs-lookup"><span data-stu-id="85ff9-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="85ff9-108">類別目錄 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="85ff9-108">Catalog Cmdlets</span></span>

<span data-ttu-id="85ff9-109">Microsoft.PowerShell.Security 模組中新增了兩個新的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="85ff9-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="85ff9-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="85ff9-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="85ff9-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="85ff9-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="85ff9-112">它們會產生並驗證 Windows 目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="85ff9-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="85ff9-113">剪貼簿 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="85ff9-113">Clipboard cmdlets</span></span>

<span data-ttu-id="85ff9-114">`Get-Clipboard`和 `Set-Clipboard` 讓您能夠更輕鬆地與 Windows PowerShell 工作階段來回傳送內容。</span><span class="sxs-lookup"><span data-stu-id="85ff9-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="85ff9-115">剪貼簿 Cmdlet 支援影像、音訊檔、檔案清單和文字。</span><span class="sxs-lookup"><span data-stu-id="85ff9-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="85ff9-116">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="85ff9-116">For more information, see:</span></span>

- [<span data-ttu-id="85ff9-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="85ff9-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="85ff9-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="85ff9-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="85ff9-119">密碼編譯訊息語法 (CMS) Cmdlet</span><span class="sxs-lookup"><span data-stu-id="85ff9-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="85ff9-120">密碼編譯訊息語法 Cmdlet 支援使用 IETF 標準格式加密和解密內容，進行密碼編譯保護訊息，如 [RFC5652](https://tools.ietf.org/html/rfc5652.html) 所述。</span><span class="sxs-lookup"><span data-stu-id="85ff9-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="85ff9-121">CMS 加密標準會實作公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀  ) 與用於解密內容的金錀 (私密金鑰  ) 不同。</span><span class="sxs-lookup"><span data-stu-id="85ff9-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="85ff9-122">公開金鑰可以廣泛共用，並非機密資料。</span><span class="sxs-lookup"><span data-stu-id="85ff9-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="85ff9-123">任何使用公開金鑰加密的內容只能使用私密金鑰來解密。</span><span class="sxs-lookup"><span data-stu-id="85ff9-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="85ff9-124">如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。</span><span class="sxs-lookup"><span data-stu-id="85ff9-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="85ff9-125">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="85ff9-125">For more information see:</span></span>

- [<span data-ttu-id="85ff9-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="85ff9-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="85ff9-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="85ff9-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="85ff9-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="85ff9-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="85ff9-129">憑證需要唯一的金鑰使用方法識別碼 (EKU) (例如「程式碼簽署」、「加密郵件」)，在 PowerShell 中將它們識別為資料加密憑證。</span><span class="sxs-lookup"><span data-stu-id="85ff9-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="85ff9-130">若要檢視憑證提供者中的文件加密憑證，您可以使用 `Get-ChildItem` 的 **DocumentEncryptionCert** 動態參數︰</span><span class="sxs-lookup"><span data-stu-id="85ff9-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="85ff9-131">從字串內容中擷取和剖析結構化物件</span><span class="sxs-lookup"><span data-stu-id="85ff9-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="85ff9-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="85ff9-132">ConvertFrom-String</span></span>

<span data-ttu-id="85ff9-133">新的 `ConvertFrom-String` Cmdlet 支援兩種模式：</span><span class="sxs-lookup"><span data-stu-id="85ff9-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="85ff9-134">基本的分隔剖析</span><span class="sxs-lookup"><span data-stu-id="85ff9-134">Basic delimited parsing</span></span>
- <span data-ttu-id="85ff9-135">自動產生的範例驅動剖析</span><span class="sxs-lookup"><span data-stu-id="85ff9-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="85ff9-136">根據預設，分隔的剖析將輸入從空白字元位置分割，並將屬性名稱指派給產生的群組。</span><span class="sxs-lookup"><span data-stu-id="85ff9-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="85ff9-137">新的 **UpdateTemplate** 參數可將學習演算法的結果儲存為範本檔案中的註解，</span><span class="sxs-lookup"><span data-stu-id="85ff9-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="85ff9-138">使得學習程序 (最慢的階段) 成為單次成本。</span><span class="sxs-lookup"><span data-stu-id="85ff9-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="85ff9-139">現在幾乎可即時使用包含已編碼學習演算法的範本來執行 `ConvertFrom-String`。</span><span class="sxs-lookup"><span data-stu-id="85ff9-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="85ff9-140">如需詳細資訊，請參閱 [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)。</span><span class="sxs-lookup"><span data-stu-id="85ff9-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="85ff9-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="85ff9-141">Convert-String</span></span>

<span data-ttu-id="85ff9-142">`Convert-String` 讓您能夠提供所需文字外觀的前後範例。</span><span class="sxs-lookup"><span data-stu-id="85ff9-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="85ff9-143">此 Cmdlet 會自動將文字格式化。</span><span class="sxs-lookup"><span data-stu-id="85ff9-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="85ff9-144">如需詳細資訊，請參閱 [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)。</span><span class="sxs-lookup"><span data-stu-id="85ff9-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="85ff9-145">FileInfo 物件的更新</span><span class="sxs-lookup"><span data-stu-id="85ff9-145">Updates to FileInfo object</span></span>

<span data-ttu-id="85ff9-146">檔案版本資訊可能產生誤導，特別是在已修補檔案的情況下。</span><span class="sxs-lookup"><span data-stu-id="85ff9-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="85ff9-147">WMF 5.0 會將新的 **FileVersionRaw** 和 **ProductVersionRaw** 指令碼屬性新增至 **FileInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="85ff9-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="85ff9-148">此處是為 powershell.exe 顯示的屬性 (假設 $pid 是 PowerShell 處理程序的識別碼) ︰</span><span class="sxs-lookup"><span data-stu-id="85ff9-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="85ff9-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="85ff9-149">Format-Hex</span></span>

<span data-ttu-id="85ff9-150">`Format-Hex` 可讓您以十六進位格式檢視文字或二進位資料。</span><span class="sxs-lookup"><span data-stu-id="85ff9-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="85ff9-151">如需詳細資訊，請參閱 [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex)。</span><span class="sxs-lookup"><span data-stu-id="85ff9-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="85ff9-152">Get-ChildItem 具有 -Depth 參數</span><span class="sxs-lookup"><span data-stu-id="85ff9-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="85ff9-153">`Get-ChildItem` 現在提供**Depth** 參數，可搭配 **Recurse** 用來限制遞迴：</span><span class="sxs-lookup"><span data-stu-id="85ff9-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="85ff9-154">宣告版本範圍 (1.\* 等等) 的模組支援</span><span class="sxs-lookup"><span data-stu-id="85ff9-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="85ff9-155">您現在可以結合 **MinimumVersion** 和 **MaximumVersion** 來匯入特定範圍內的模組。</span><span class="sxs-lookup"><span data-stu-id="85ff9-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="85ff9-156">參數也支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="85ff9-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="85ff9-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="85ff9-157">New-Guid</span></span>

<span data-ttu-id="85ff9-158">有許多您需要使用唯一識別碼的案例。</span><span class="sxs-lookup"><span data-stu-id="85ff9-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="85ff9-159">`New-GUID` Cmdlet 提供一個簡單的方式來建立新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="85ff9-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="85ff9-160">NoNewLine 參數</span><span class="sxs-lookup"><span data-stu-id="85ff9-160">NoNewLine parameter</span></span>

<span data-ttu-id="85ff9-161">`Out-File`、`Add-Content` 及 `Set-Content` 現在提供新的 **NoNewline** 參數來省略輸出之後的新行。</span><span class="sxs-lookup"><span data-stu-id="85ff9-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="85ff9-162">例如：</span><span class="sxs-lookup"><span data-stu-id="85ff9-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="85ff9-163">如未指定 **NoNewline**，每個片段都會放在不同行：</span><span class="sxs-lookup"><span data-stu-id="85ff9-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="85ff9-164">使用改進的 Item Cmdlet 與符號連結互動</span><span class="sxs-lookup"><span data-stu-id="85ff9-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="85ff9-165">已擴充 Item Cmdlet 和數個相關的 Cmdlet 來支援符號連結。</span><span class="sxs-lookup"><span data-stu-id="85ff9-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="85ff9-166">符號連結檔案</span><span class="sxs-lookup"><span data-stu-id="85ff9-166">Symbolic link files</span></span>

<span data-ttu-id="85ff9-167">在此範例中，我們會在 C:\Temp 中建立名為 MySymLinkFile.txt 的新符號連結檔案，其會連結至 $pshome\profile.ps1。</span><span class="sxs-lookup"><span data-stu-id="85ff9-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="85ff9-168">這三個範例全都會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="85ff9-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="85ff9-169">符號連結目錄</span><span class="sxs-lookup"><span data-stu-id="85ff9-169">Symbolic link directories</span></span>

<span data-ttu-id="85ff9-170">在此範例中，我們會在 C:\Temp 中建立名為 MySymLinkDir 的新符號連結目錄，其會連結至 $pshome 資料夾。</span><span class="sxs-lookup"><span data-stu-id="85ff9-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="85ff9-171">這三個範例全都會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="85ff9-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="85ff9-172">永久連結</span><span class="sxs-lookup"><span data-stu-id="85ff9-172">Hard links</span></span>

<span data-ttu-id="85ff9-173">允許相同的**路徑**和**名稱**組合，如前所述。</span><span class="sxs-lookup"><span data-stu-id="85ff9-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="85ff9-174">目錄接合</span><span class="sxs-lookup"><span data-stu-id="85ff9-174">Directory junctions</span></span>

<span data-ttu-id="85ff9-175">允許相同的**路徑**和**名稱**組合，如前所述。</span><span class="sxs-lookup"><span data-stu-id="85ff9-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="85ff9-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="85ff9-176">Get-ChildItem</span></span>

<span data-ttu-id="85ff9-177">`Get-ChildItem` 現在會在 **Mode** 屬性中顯示 'l'，以指出符號連結檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="85ff9-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="85ff9-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="85ff9-178">Remove-Item</span></span>

<span data-ttu-id="85ff9-179">移除符號連結的運作方式類似移除任何其他項目類型。</span><span class="sxs-lookup"><span data-stu-id="85ff9-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="85ff9-180">使用 **Force** 參數來移除目標目錄中的檔案和符號連結。</span><span class="sxs-lookup"><span data-stu-id="85ff9-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="85ff9-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="85ff9-181">New-TemporaryFile</span></span>

<span data-ttu-id="85ff9-182">有時候在您的指令碼中，您必須建立暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="85ff9-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="85ff9-183">您可以使用 `New-TemporaryFile` Cmdlet 來進行此作業：</span><span class="sxs-lookup"><span data-stu-id="85ff9-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="85ff9-184">使用 PowerShell 管理網路交換器</span><span class="sxs-lookup"><span data-stu-id="85ff9-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="85ff9-185">網路交換器 Cmdlet，在 WMF 5.0 中引進，可讓您將交換器、虛擬 LAN (VLAN) 和基本層級 2 網路交換器連接埠設定套用至 Windows Server 2012 R2 標誌認證的網路交換器。</span><span class="sxs-lookup"><span data-stu-id="85ff9-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="85ff9-186">使用這些 Cmdlet 可以執行︰</span><span class="sxs-lookup"><span data-stu-id="85ff9-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="85ff9-187">全域交換器設定，例如︰</span><span class="sxs-lookup"><span data-stu-id="85ff9-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="85ff9-188">設定主機名稱</span><span class="sxs-lookup"><span data-stu-id="85ff9-188">Set host name</span></span>
  - <span data-ttu-id="85ff9-189">設定參數橫幅</span><span class="sxs-lookup"><span data-stu-id="85ff9-189">Set switch banner</span></span>
  - <span data-ttu-id="85ff9-190">保存設定</span><span class="sxs-lookup"><span data-stu-id="85ff9-190">Persist configuration</span></span>
  - <span data-ttu-id="85ff9-191">啟用或停用功能</span><span class="sxs-lookup"><span data-stu-id="85ff9-191">Enable or disable feature</span></span>

- <span data-ttu-id="85ff9-192">VLAN 設定：</span><span class="sxs-lookup"><span data-stu-id="85ff9-192">VLAN configuration:</span></span>
  - <span data-ttu-id="85ff9-193">建立或移除 VLAN</span><span class="sxs-lookup"><span data-stu-id="85ff9-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="85ff9-194">啟用或停用 VLAN</span><span class="sxs-lookup"><span data-stu-id="85ff9-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="85ff9-195">列舉 VLAN</span><span class="sxs-lookup"><span data-stu-id="85ff9-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="85ff9-196">設定易記的 VLAN 名稱</span><span class="sxs-lookup"><span data-stu-id="85ff9-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="85ff9-197">階層 2 連接埠設定：</span><span class="sxs-lookup"><span data-stu-id="85ff9-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="85ff9-198">列舉連接埠</span><span class="sxs-lookup"><span data-stu-id="85ff9-198">Enumerate ports</span></span>
  - <span data-ttu-id="85ff9-199">啟用或停用連接埠</span><span class="sxs-lookup"><span data-stu-id="85ff9-199">Enable or disable ports</span></span>
  - <span data-ttu-id="85ff9-200">設定連接埠模式和屬性</span><span class="sxs-lookup"><span data-stu-id="85ff9-200">Set port modes and properties</span></span>
  - <span data-ttu-id="85ff9-201">將 VLAN 加入連接埠的主幹或存取或建立關聯性</span><span class="sxs-lookup"><span data-stu-id="85ff9-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="85ff9-202">如需詳細資訊，請參閱 [NetworkSwitchManager](/powershell/module/networkswitchmanager/) 文件。</span><span class="sxs-lookup"><span data-stu-id="85ff9-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="85ff9-203">根據具有 ODataUtils 的 OData 端點產生 PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="85ff9-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="85ff9-204">ODataUtils 模組允許從支援 OData 的 REST 端點產生 PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="85ff9-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="85ff9-205">Microsoft.PowerShell.ODataUtils 模組包括下列功能：</span><span class="sxs-lookup"><span data-stu-id="85ff9-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="85ff9-206">從伺服器端端點到用戶端的通道其他資訊。</span><span class="sxs-lookup"><span data-stu-id="85ff9-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="85ff9-207">用戶端的分頁支援</span><span class="sxs-lookup"><span data-stu-id="85ff9-207">Client-side paging support</span></span>
- <span data-ttu-id="85ff9-208">使用 -Select 參數進行伺服器端篩選</span><span class="sxs-lookup"><span data-stu-id="85ff9-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="85ff9-209">Web 要求標頭的支援</span><span class="sxs-lookup"><span data-stu-id="85ff9-209">Support for web request headers</span></span>

<span data-ttu-id="85ff9-210">`Export-ODataEndPointProxy` Cmdlet 所產生的 Proxy Cmdlet 可提供來自**資訊**串流上伺服器端 OData 端點的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="85ff9-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="85ff9-211">在下列範例中，我們要擷取熱門產品，並擷取 `$infoStream` 變數中的輸出。</span><span class="sxs-lookup"><span data-stu-id="85ff9-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="85ff9-212">藉由指定 **IncludeTotalResponseCount** 參數，我們會取得伺服器上可用之所有**產品**記錄的總計數。</span><span class="sxs-lookup"><span data-stu-id="85ff9-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="85ff9-213">您可以使用用戶端分頁支援，以批次方式從伺服器端取得記錄。</span><span class="sxs-lookup"><span data-stu-id="85ff9-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="85ff9-214">當您必須透過網路從伺服器取得大量資料時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="85ff9-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="85ff9-215">產生的 Proxy Cmdlet 支援 **Select** 參數，此參數可用來作為篩選條件，以便只接收用戶端所需的記錄屬性。</span><span class="sxs-lookup"><span data-stu-id="85ff9-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="85ff9-216">篩選會在伺服器上發生，以減少透過網路傳送的資料量。</span><span class="sxs-lookup"><span data-stu-id="85ff9-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="85ff9-217">`Export-ODataEndpointProxy` Cmdlet (及其產生的 Proxy Cmdlet) 現在均支援 **Headers** 參數。</span><span class="sxs-lookup"><span data-stu-id="85ff9-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="85ff9-218">標頭可用來傳遞 OData 端點所預期的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="85ff9-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="85ff9-219">在下列範例中，會將包含訂用帳戶金鑰的雜湊表提供給 **Headers** 參數。</span><span class="sxs-lookup"><span data-stu-id="85ff9-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="85ff9-220">這是預期訂用帳戶金鑰進行驗證的典型服務範例。</span><span class="sxs-lookup"><span data-stu-id="85ff9-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
