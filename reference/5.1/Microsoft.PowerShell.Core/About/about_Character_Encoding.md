---
title: about_Character_Encoding
description: 描述 PowerShell 如何針對字串資料的輸入和輸出使用字元編碼。
ms.date: 10/21/2020
Locale: en-US
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
ms.openlocfilehash: 3067a97a00da6f6f759ad874f98c06fe7ad6d923
ms.sourcegitcommit: df80c558e9a4b89c9798f084bd04012ece15155c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "93208859"
---
# <a name="about_character_encoding"></a><span data-ttu-id="c23cf-103">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="c23cf-103">about_Character_Encoding</span></span>

## <a name="short-description"></a><span data-ttu-id="c23cf-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="c23cf-104">Short description</span></span>
<span data-ttu-id="c23cf-105">描述 PowerShell 如何針對字串資料的輸入和輸出使用字元編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-105">Describes how PowerShell uses character encoding for input and output of string data.</span></span>

## <a name="long-description"></a><span data-ttu-id="c23cf-106">完整描述</span><span class="sxs-lookup"><span data-stu-id="c23cf-106">Long description</span></span>

<span data-ttu-id="c23cf-107">Unicode 是全球字元編碼標準。</span><span class="sxs-lookup"><span data-stu-id="c23cf-107">Unicode is a worldwide character-encoding standard.</span></span> <span data-ttu-id="c23cf-108">系統會專門針對字元和字串操作使用 Unicode。</span><span class="sxs-lookup"><span data-stu-id="c23cf-108">The system uses Unicode exclusively for character and string manipulation.</span></span> <span data-ttu-id="c23cf-109">如需 Unicode 所有方面的詳細說明，請參閱 [Unicode 標準](https://www.unicode.org/standard/standard.html)。</span><span class="sxs-lookup"><span data-stu-id="c23cf-109">For a detailed description of all aspects of Unicode, refer to [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>

<span data-ttu-id="c23cf-110">Windows 支援 Unicode 和傳統字元集。</span><span class="sxs-lookup"><span data-stu-id="c23cf-110">Windows supports Unicode and traditional character sets.</span></span> <span data-ttu-id="c23cf-111">傳統字元集（例如 Windows 字碼頁）使用8位值或8位值的組合來代表特定語言或地理區域設定中使用的字元。</span><span class="sxs-lookup"><span data-stu-id="c23cf-111">Traditional character sets, such as Windows code pages, use 8-bit values or combinations of 8-bit values to represent the characters used in a specific language or geographical region settings.</span></span>

<span data-ttu-id="c23cf-112">PowerShell 預設會使用 Unicode 字元集。</span><span class="sxs-lookup"><span data-stu-id="c23cf-112">PowerShell uses a Unicode character set by default.</span></span> <span data-ttu-id="c23cf-113">不過，有數個 Cmdlet 具有可指定不同字元集編碼的 **編碼** 參數。</span><span class="sxs-lookup"><span data-stu-id="c23cf-113">However, several cmdlets have an **Encoding** parameter that can specify encoding for a different character set.</span></span> <span data-ttu-id="c23cf-114">此參數可讓您選擇所需的字元編碼方式，以與其他系統和應用程式交互操作。</span><span class="sxs-lookup"><span data-stu-id="c23cf-114">This parameter allows you to choose the specific the character encoding you need for interoperability with other systems and applications.</span></span>

<span data-ttu-id="c23cf-115">下列 Cmdlet 具有 **Encoding** 參數：</span><span class="sxs-lookup"><span data-stu-id="c23cf-115">The following cmdlets have the **Encoding** parameter:</span></span>

- <span data-ttu-id="c23cf-116">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="c23cf-116">Microsoft.PowerShell.Management</span></span>
  - <span data-ttu-id="c23cf-117">Add-Content</span><span class="sxs-lookup"><span data-stu-id="c23cf-117">Add-Content</span></span>
  - <span data-ttu-id="c23cf-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="c23cf-118">Get-Content</span></span>
  - <span data-ttu-id="c23cf-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="c23cf-119">Set-Content</span></span>
- <span data-ttu-id="c23cf-120">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="c23cf-120">Microsoft.PowerShell.Utility</span></span>
  - <span data-ttu-id="c23cf-121">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="c23cf-121">Export-Clixml</span></span>
  - <span data-ttu-id="c23cf-122">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="c23cf-122">Export-Csv</span></span>
  - <span data-ttu-id="c23cf-123">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="c23cf-123">Export-PSSession</span></span>
  - <span data-ttu-id="c23cf-124">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="c23cf-124">Format-Hex</span></span>
  - <span data-ttu-id="c23cf-125">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="c23cf-125">Import-Csv</span></span>
  - <span data-ttu-id="c23cf-126">Out-File</span><span class="sxs-lookup"><span data-stu-id="c23cf-126">Out-File</span></span>
  - <span data-ttu-id="c23cf-127">Select-String</span><span class="sxs-lookup"><span data-stu-id="c23cf-127">Select-String</span></span>
  - <span data-ttu-id="c23cf-128">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="c23cf-128">Send-MailMessage</span></span>

## <a name="the-byte-order-mark"></a><span data-ttu-id="c23cf-129">位元組順序標記</span><span class="sxs-lookup"><span data-stu-id="c23cf-129">The byte-order-mark</span></span>

<span data-ttu-id="c23cf-130">位元組順序標記 (BOM) 是在檔案或文字資料流程的前幾個位元組中的 _unicode_ 簽章，指出用於資料的 unicode 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-130">The byte-order-mark (BOM) is a _Unicode signature_ in the first few bytes of a file or text stream that indicate which Unicode encoding used for the data.</span></span> <span data-ttu-id="c23cf-131">如需詳細資訊，請參閱維琪百科中的 [位元組順序標記](https://wikipedia.org/wiki/Byte_order_mark) 文章。</span><span class="sxs-lookup"><span data-stu-id="c23cf-131">For more information, see the [Byte order mark](https://wikipedia.org/wiki/Byte_order_mark) article in Wikipedia.</span></span>

<span data-ttu-id="c23cf-132">在 Windows PowerShell 中，除了以外的任何 Unicode 編碼 `UTF7` 一律會建立 BOM。</span><span class="sxs-lookup"><span data-stu-id="c23cf-132">In Windows PowerShell, any Unicode encoding, except `UTF7`, always creates a BOM.</span></span> <span data-ttu-id="c23cf-133">`utf8NoBOM`所有文字輸出的 PowerShell Core 預設為。</span><span class="sxs-lookup"><span data-stu-id="c23cf-133">PowerShell Core defaults to `utf8NoBOM` for all text output.</span></span>

<span data-ttu-id="c23cf-134">為了獲得最佳的整體相容性，請避免在 UTF-8 檔案中使用 Bom。</span><span class="sxs-lookup"><span data-stu-id="c23cf-134">For best overall compatibility, avoid using BOMs in UTF-8 files.</span></span> <span data-ttu-id="c23cf-135">適用于 Windows 平臺的 unix 平臺和 Unix 遺產公用程式也不支援 Bom。</span><span class="sxs-lookup"><span data-stu-id="c23cf-135">Unix platforms and Unix-heritage utilities also used on Windows Platforms don't support BOMs.</span></span>

<span data-ttu-id="c23cf-136">同樣地， `UTF7` 應該避免編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-136">Similarly, `UTF7` encoding should be avoided.</span></span> <span data-ttu-id="c23cf-137">UTF-7 不是標準的 Unicode 編碼方式，而且在所有版本的 PowerShell 中都不會使用 BOM 來撰寫。</span><span class="sxs-lookup"><span data-stu-id="c23cf-137">UTF-7 is not a standard Unicode encoding and is written without a BOM in all versions of PowerShell.</span></span>

<span data-ttu-id="c23cf-138">在類似 Unix 的平臺上建立 PowerShell 腳本，或在 Windows 上使用跨平臺編輯器（例如 Visual Studio Code），會產生使用編碼的檔案 `UTF8NoBOM` 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-138">Creating PowerShell scripts on a Unix-like platform or using a cross-platform editor on Windows, such as Visual Studio Code, results in a file encoded using `UTF8NoBOM`.</span></span> <span data-ttu-id="c23cf-139">這些檔案在 PowerShell Core 上可正常運作，但如果檔案包含非 Ascii 字元，則可能會在 Windows PowerShell 中中斷。</span><span class="sxs-lookup"><span data-stu-id="c23cf-139">These files work fine on PowerShell Core, but may break in Windows PowerShell if the file contains non-Ascii characters.</span></span>

<span data-ttu-id="c23cf-140">如果您需要在腳本中使用非 Ascii 字元，請將它們儲存為 UTF-8 與 BOM。</span><span class="sxs-lookup"><span data-stu-id="c23cf-140">If you need to use non-Ascii characters in your scripts, save them as UTF-8 with BOM.</span></span> <span data-ttu-id="c23cf-141">如果沒有 BOM，Windows PowerShell 會將腳本誤譯為舊版 "ANSI" 字碼頁中的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-141">Without the BOM, Windows PowerShell misinterprets your script as being encoded in the legacy "ANSI" codepage.</span></span> <span data-ttu-id="c23cf-142">相反地，具有 UTF-8 BOM 的檔案在類似 Unix 的平臺上可能會有問題。</span><span class="sxs-lookup"><span data-stu-id="c23cf-142">Conversely, files that do have the UTF-8 BOM can be problematic on Unix-like platforms.</span></span> <span data-ttu-id="c23cf-143">許多 Unix 工具，例如 `cat` 、 `sed` 、 `awk` 和某些編輯器，例如 `gedit` 不知道如何處理 BOM。</span><span class="sxs-lookup"><span data-stu-id="c23cf-143">Many Unix tools such as `cat`, `sed`, `awk`, and some editors such as `gedit` don't know how to treat the BOM.</span></span>

## <a name="character-encoding-in-windows-powershell"></a><span data-ttu-id="c23cf-144">Windows PowerShell 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="c23cf-144">Character encoding in Windows PowerShell</span></span>

<span data-ttu-id="c23cf-145">在 PowerShell 5.1 中， **編碼** 參數支援下列值：</span><span class="sxs-lookup"><span data-stu-id="c23cf-145">In PowerShell 5.1, the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="c23cf-146">`Ascii` 使用 Ascii (7 位) 字元集。</span><span class="sxs-lookup"><span data-stu-id="c23cf-146">`Ascii` Uses Ascii (7-bit) character set.</span></span>
- <span data-ttu-id="c23cf-147">`BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="c23cf-147">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="c23cf-148">`BigEndianUTF32` 使用具有位元組由大到小的 32 UTF-8 順序。</span><span class="sxs-lookup"><span data-stu-id="c23cf-148">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="c23cf-149">`Byte` 將一組字元編碼成位元組序列。</span><span class="sxs-lookup"><span data-stu-id="c23cf-149">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="c23cf-150">`Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-150">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="c23cf-151">`Oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-151">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="c23cf-152">`String`：與 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="c23cf-152">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="c23cf-153">`Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。</span><span class="sxs-lookup"><span data-stu-id="c23cf-153">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="c23cf-154">`Unknown`：與 `Unicode` 相同。</span><span class="sxs-lookup"><span data-stu-id="c23cf-154">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="c23cf-155">`UTF32` 以位元組由小到大的位元組順序使用 UTF-32。</span><span class="sxs-lookup"><span data-stu-id="c23cf-155">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>
- <span data-ttu-id="c23cf-156">`UTF7` 使用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="c23cf-156">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="c23cf-157">`UTF8` 使用 UTF-8 (搭配 BOM) 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-157">`UTF8` Uses UTF-8 (with BOM).</span></span>

<span data-ttu-id="c23cf-158">一般而言，Windows PowerShell 預設會使用 Unicode [utf-16le](https://wikipedia.org/wiki/UTF-16) 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-158">In general, Windows PowerShell uses the Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) encoding by default.</span></span> <span data-ttu-id="c23cf-159">不過，Windows PowerShell 中的 Cmdlet 所使用的預設編碼方式不一致。</span><span class="sxs-lookup"><span data-stu-id="c23cf-159">However, the default encoding used by cmdlets in Windows PowerShell is not consistent.</span></span>

> [!NOTE]
> <span data-ttu-id="c23cf-160">除了以外，使用任何 Unicode 編碼 `UTF7` 一律會建立 BOM。</span><span class="sxs-lookup"><span data-stu-id="c23cf-160">Using any Unicode encoding, except `UTF7`, always creates a BOM.</span></span>

<span data-ttu-id="c23cf-161">針對將輸出寫入檔案的 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="c23cf-161">For cmdlets that write output to files:</span></span>

- <span data-ttu-id="c23cf-162">`Out-File` 以及重新導向運算子 `>` 和 `>>` 建立 utf-16le，這一點與 `Set-Content` 和不同 `Add-Content` 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-162">`Out-File` and the redirection operators `>` and `>>` create UTF-16LE, which notably differs from `Set-Content` and `Add-Content`.</span></span>

- <span data-ttu-id="c23cf-163">`New-ModuleManifest``Export-CliXml`此外也會建立 utf-16le 檔案。</span><span class="sxs-lookup"><span data-stu-id="c23cf-163">`New-ModuleManifest` and `Export-CliXml` also create UTF-16LE files.</span></span>

- <span data-ttu-id="c23cf-164">當目標檔案為空白或不存在時， `Set-Content` 請 `Add-Content` 使用 `Default` 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-164">When the target file is empty or doesn't exist, `Set-Content` and `Add-Content` use `Default` encoding.</span></span> <span data-ttu-id="c23cf-165">`Default` 這是使用中系統地區設定的 ANSI 舊版字碼頁所指定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-165">`Default` is the encoding specified by the active system locale's ANSI legacy code page.</span></span>

- <span data-ttu-id="c23cf-166">`Export-Csv` 建立檔案 `Ascii` ，但使用 **附加** 參數時使用不同的編碼 (請參閱下面的) 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-166">`Export-Csv` creates `Ascii` files but uses different encoding when using **Append** parameter (see below).</span></span>

- <span data-ttu-id="c23cf-167">`Export-PSSession` 預設會建立具有 BOM 的 UTF-8 檔案。</span><span class="sxs-lookup"><span data-stu-id="c23cf-167">`Export-PSSession` creates UTF-8 files with BOM by default.</span></span>

- <span data-ttu-id="c23cf-168">`New-Item -Type File -Value` 建立不使用 BOM 的 UTF-8 檔案。</span><span class="sxs-lookup"><span data-stu-id="c23cf-168">`New-Item -Type File -Value` creates a BOM-less UTF-8 file.</span></span>

- <span data-ttu-id="c23cf-169">`Send-MailMessage` 預設會使用 `Default` 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-169">`Send-MailMessage` uses `Default` encoding by default.</span></span>

- <span data-ttu-id="c23cf-170">`Start-Transcript``Utf8`使用 BOM 建立檔案。</span><span class="sxs-lookup"><span data-stu-id="c23cf-170">`Start-Transcript` creates `Utf8` files with a BOM.</span></span> <span data-ttu-id="c23cf-171">使用 **Append** 參數時，編碼可能會不同 (請參閱下面的) 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-171">When the **Append** parameter is used, the encoding can be different (see below).</span></span>

<span data-ttu-id="c23cf-172">針對附加至現有檔案的命令：</span><span class="sxs-lookup"><span data-stu-id="c23cf-172">For commands that append to an existing file:</span></span>

- <span data-ttu-id="c23cf-173">`Out-File -Append` 而重新導向 `>>` 運算子不會嘗試比對現有目標檔案內容的編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-173">`Out-File -Append` and the `>>` redirection operator make no attempt to match the encoding of the existing target file's content.</span></span> <span data-ttu-id="c23cf-174">相反地，除非使用 **encoding** 參數，否則會使用預設的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-174">Instead, they use the default encoding unless the **Encoding** parameter is used.</span></span> <span data-ttu-id="c23cf-175">附加內容時，您必須使用原始檔編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-175">You must use the files original encoding when appending content.</span></span>

- <span data-ttu-id="c23cf-176">如果沒有明確的 **編碼** 參數，則 `Add-Content` 會偵測現有的編碼，並自動將它套用至新的內容。</span><span class="sxs-lookup"><span data-stu-id="c23cf-176">In the absence of an explicit **Encoding** parameter, `Add-Content` detects the existing encoding and automatically applies it to the new content.</span></span> <span data-ttu-id="c23cf-177">如果現有的內容沒有 BOM， `Default` 則會使用 ANSI 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-177">If the existing content has no BOM, `Default` ANSI encoding is used.</span></span> <span data-ttu-id="c23cf-178">`Add-Content`在 PowerShell Core (v6 和更新) 版本中的行為相同，除非預設編碼為 `Utf8` 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-178">The behavior of `Add-Content` is the same in PowerShell Core (v6 and higher) except the default encoding is `Utf8`.</span></span>

- <span data-ttu-id="c23cf-179">`Export-Csv -Append` 當目標檔案包含 BOM 時，符合現有的編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-179">`Export-Csv -Append` matches the existing encoding when the target file contains a BOM.</span></span> <span data-ttu-id="c23cf-180">如果 BOM 不存在，就會使用 `Utf8` 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-180">In the absence of a BOM, it uses `Utf8` encoding.</span></span>

- <span data-ttu-id="c23cf-181">`Start-Transcript -Append` 符合包含 BOM 之檔案的現有編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-181">`Start-Transcript -Append` matches the existing encoding of files that include a BOM.</span></span> <span data-ttu-id="c23cf-182">當 BOM 不存在時，它會預設為 `Ascii` 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-182">In the absence of a BOM, it defaults to `Ascii` encoding.</span></span> <span data-ttu-id="c23cf-183">當文字記錄中的資料包含多位元組字元時，此編碼可能會導致資料遺失或字元損毀。</span><span class="sxs-lookup"><span data-stu-id="c23cf-183">This encoding can result in data loss or character corruption when the data in the transcript contains multibyte characters.</span></span>

<span data-ttu-id="c23cf-184">針對在缺少 BOM 時讀取字串資料的 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="c23cf-184">For cmdlets that read string data in the absence of a BOM:</span></span>

- <span data-ttu-id="c23cf-185">`Get-Content` 和 `Import-PowerShellDataFile` 使用 `Default` ANSI 編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-185">`Get-Content` and `Import-PowerShellDataFile` uses the `Default` ANSI encoding.</span></span> <span data-ttu-id="c23cf-186">當 PowerShell 引擎從檔案讀取原始程式碼時，也會使用 ANSI。</span><span class="sxs-lookup"><span data-stu-id="c23cf-186">ANSI is also what the PowerShell engine uses when it reads source code from files.</span></span>

- <span data-ttu-id="c23cf-187">`Import-Csv`、 `Import-CliXml` 和 `Select-String` 假設 `Utf8` 沒有 BOM。</span><span class="sxs-lookup"><span data-stu-id="c23cf-187">`Import-Csv`, `Import-CliXml`, and `Select-String` assume `Utf8` in the absence of a BOM.</span></span>

## <a name="character-encoding-in-powershell-core"></a><span data-ttu-id="c23cf-188">PowerShell Core 中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="c23cf-188">Character encoding in PowerShell Core</span></span>

<span data-ttu-id="c23cf-189">在 PowerShell Core (v6 和更新版本的) 中， **Encoding** 參數支援下列值：</span><span class="sxs-lookup"><span data-stu-id="c23cf-189">In PowerShell Core (v6 and higher), the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="c23cf-190">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-190">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c23cf-191">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-191">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c23cf-192">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-192">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c23cf-193">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-193">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c23cf-194">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-194">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c23cf-195">`utf8`：以 UTF-8 格式編碼 (沒有 BOM) 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-195">`utf8`: Encodes in UTF-8 format (no BOM).</span></span>
- <span data-ttu-id="c23cf-196">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="c23cf-196">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c23cf-197">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="c23cf-197">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c23cf-198">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c23cf-198">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c23cf-199">`utf8NoBOM`針對所有輸出 PowerShell Core 預設為。</span><span class="sxs-lookup"><span data-stu-id="c23cf-199">PowerShell Core defaults to `utf8NoBOM` for all output.</span></span>

<span data-ttu-id="c23cf-200">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="c23cf-200">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c23cf-201">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage)。</span><span class="sxs-lookup"><span data-stu-id="c23cf-201">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage).</span></span>

## <a name="changing-the-default-encoding"></a><span data-ttu-id="c23cf-202">變更預設編碼</span><span class="sxs-lookup"><span data-stu-id="c23cf-202">Changing the default encoding</span></span>

<span data-ttu-id="c23cf-203">PowerShell 有兩個可以用來變更預設編碼行為的預設變數。</span><span class="sxs-lookup"><span data-stu-id="c23cf-203">PowerShell has two default variables that can be used to change the default encoding behavior.</span></span>

- `$PSDefaultParameterValues`
- `$OutputEncoding`

<span data-ttu-id="c23cf-204">如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c23cf-204">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="c23cf-205">從 PowerShell 5.1 開始，重新導向操作員 (`>` ， `>>`) 呼叫 `Out-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c23cf-205">Beginning in PowerShell 5.1, the redirection operators (`>` and `>>`) call the `Out-File` cmdlet.</span></span> <span data-ttu-id="c23cf-206">因此，您可以使用喜好設定變數來設定預設的編碼方式， `$PSDefaultParameterValues` 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c23cf-206">Therefore, you can set the default encoding of them using the `$PSDefaultParameterValues` preference variable as shown in this example:</span></span>

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

<span data-ttu-id="c23cf-207">使用下列語句來變更所有具有 **encoding** 參數之 Cmdlet 的預設編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-207">Use the following statement to change the default encoding for all cmdlets that have the **Encoding** parameter.</span></span>

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> <span data-ttu-id="c23cf-208">將此命令放入 PowerShell 設定檔中，會讓喜好設定成為會話全域設定，此設定會影響未明確指定編碼的所有命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="c23cf-208">Putting this command in your PowerShell profile makes the preference a session-global setting that affects all commands and scripts that do not explicitly specify an encoding.</span></span>
>
> <span data-ttu-id="c23cf-209">同樣地，您應該將這類命令包含在您想要以相同方式行為的腳本或模組中。</span><span class="sxs-lookup"><span data-stu-id="c23cf-209">Similarly, you should include such commands in your scripts or modules that you want to behave the same way.</span></span> <span data-ttu-id="c23cf-210">使用這些命令可確保 Cmdlet 的行為方式，甚至是在其他使用者執行時、在不同的電腦上，或在不同版本的 PowerShell 中執行。</span><span class="sxs-lookup"><span data-stu-id="c23cf-210">Using these commands ensure that cmdlets behave the same way even when run by another user, on a different computer, or in a different version of PowerShell.</span></span>

<span data-ttu-id="c23cf-211">自動變數 `$OutputEncoding` 會影響 PowerShell 用來與外部程式通訊的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-211">The automatic variable `$OutputEncoding` affects the encoding PowerShell uses to communicate with external programs.</span></span> <span data-ttu-id="c23cf-212">它不會影響輸出重新導向運算子和 PowerShell Cmdlet 用來儲存至檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c23cf-212">It has no effect on the encoding that the output redirection operators and PowerShell cmdlets use to save to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="c23cf-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c23cf-213">See also</span></span>

- [<span data-ttu-id="c23cf-214">.NET 中的字元編碼簡介</span><span class="sxs-lookup"><span data-stu-id="c23cf-214">Introduction to character encoding in .NET</span></span>](/dotnet/standard/base-types/character-encoding-introduction)
- [<span data-ttu-id="c23cf-215">字碼頁-Win32 應用程式</span><span class="sxs-lookup"><span data-stu-id="c23cf-215">Code Pages - Win32 apps</span></span>](/windows/win32/intl/code-pages)
- [<span data-ttu-id="c23cf-216">Unicode 標準</span><span class="sxs-lookup"><span data-stu-id="c23cf-216">The Unicode Standard</span></span>](https://www.unicode.org/standard/standard.html)
- [<span data-ttu-id="c23cf-217">編碼。字碼頁</span><span class="sxs-lookup"><span data-stu-id="c23cf-217">Encoding.CodePage</span></span>](/dotnet/api/system.text.encoding.codepage)
- [<span data-ttu-id="c23cf-218">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="c23cf-218">UTF-16LE</span></span>](https://wikipedia.org/wiki/UTF-16)
- [<span data-ttu-id="c23cf-219">位元組順序標記</span><span class="sxs-lookup"><span data-stu-id="c23cf-219">Byte order mark</span></span>](https://wikipedia.org/wiki/Byte_order_mark)
- [<span data-ttu-id="c23cf-220">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="c23cf-220">about_Preference_Variables</span></span>](about_Preference_Variables.md)
