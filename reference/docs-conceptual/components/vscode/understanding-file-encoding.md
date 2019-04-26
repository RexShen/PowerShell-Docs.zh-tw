---
title: 了解 VSCode 與 PowerShell 中的檔案編碼
description: 設定 VSCode 與 PowerShell 中的檔案編碼
ms.date: 02/28/2019
ms.openlocfilehash: 6a00e45b3700f72f78e2fbcdf6e317f3a17b53c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058432"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="1fa49-103">了解 VSCode 與 PowerShell 中的檔案編碼</span><span class="sxs-lookup"><span data-stu-id="1fa49-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="1fa49-104">使用 VS Code 建立和編輯 PowerShell 指令碼時，請務必使用正確的字元編碼格式來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="1fa49-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="1fa49-105">什麼是檔案編碼，以及它為何如此重要？</span><span class="sxs-lookup"><span data-stu-id="1fa49-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="1fa49-106">VSCode 管理緩衝區中人工輸入的字元字串和檔案系統位元組之讀取/寫入區塊間的介面。</span><span class="sxs-lookup"><span data-stu-id="1fa49-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="1fa49-107">當 VSCode 儲存檔案時，它會使用文字編碼來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="1fa49-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="1fa49-108">同樣地，當 PowerShell 執行指令碼時，它必須將檔案中的位元組轉換成字元，以在 PowerShell 程式中重建檔案。</span><span class="sxs-lookup"><span data-stu-id="1fa49-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="1fa49-109">因為 VSCode 寫入檔案，而 PowerShell 讀取檔案，所以它們需要使用相同的編碼系統。</span><span class="sxs-lookup"><span data-stu-id="1fa49-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="1fa49-110">這個剖析 PowerShell 指令碼的程序為：*位元組*  ->  *字元*  ->  *權杖*  ->  *抽象語法樹*  ->  *執行*。</span><span class="sxs-lookup"><span data-stu-id="1fa49-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="1fa49-111">VSCode 和 PowerShell 都使用合理的預設編碼設定來安裝。</span><span class="sxs-lookup"><span data-stu-id="1fa49-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="1fa49-112">不過，PowerShell 使用的預設編碼已隨著 PowerShell Core (v6.x) 發行而變更。</span><span class="sxs-lookup"><span data-stu-id="1fa49-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="1fa49-113">為確保在 VSCode 中使用 PowerShell 或 PowerShell 延伸模組時沒有任何問題，您需要正確設定 VSCode 和 PowerShell 設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="1fa49-114">編碼問題常見原因</span><span class="sxs-lookup"><span data-stu-id="1fa49-114">Common causes of encoding issues</span></span>

<span data-ttu-id="1fa49-115">當 VSCode 或指令碼檔案編碼不符 PowerShell 的預期編碼時，會發生編碼問題。</span><span class="sxs-lookup"><span data-stu-id="1fa49-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="1fa49-116">PowerShell 無法自動判斷檔案編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="1fa49-117">使用非 [7 位元 ASCII 字元集](https://ascii.cl/)字元時，最可能發生編碼問題。</span><span class="sxs-lookup"><span data-stu-id="1fa49-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="1fa49-118">例如：</span><span class="sxs-lookup"><span data-stu-id="1fa49-118">For example:</span></span>

- <span data-ttu-id="1fa49-119">有重音符號的拉丁字元 (`É`、`ü`)</span><span class="sxs-lookup"><span data-stu-id="1fa49-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="1fa49-120">斯拉夫文等非拉丁字元 (`Д`、`Ц`)</span><span class="sxs-lookup"><span data-stu-id="1fa49-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="1fa49-121">中文漢字 (`脚`、`本`)</span><span class="sxs-lookup"><span data-stu-id="1fa49-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="1fa49-122">編碼問題的常見原因如下：</span><span class="sxs-lookup"><span data-stu-id="1fa49-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="1fa49-123">VSCode 和 PowerShell 的編碼不是從其預設值變更。</span><span class="sxs-lookup"><span data-stu-id="1fa49-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="1fa49-124">PowerShell 5.1 及之前的版本，其預設編碼和 VSCode 不同。</span><span class="sxs-lookup"><span data-stu-id="1fa49-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="1fa49-125">另一個編輯器已開啟，並以新的編碼覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="1fa49-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="1fa49-126">這通常發生在 ISE。</span><span class="sxs-lookup"><span data-stu-id="1fa49-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="1fa49-127">檔案已簽入和 VSCode 或 PowerShell 預期不同之編碼的原始檔控制中。</span><span class="sxs-lookup"><span data-stu-id="1fa49-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="1fa49-128">當共同作業者使用不同編碼設定的編輯器時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="1fa49-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="1fa49-129">如何分辨發生編碼問題</span><span class="sxs-lookup"><span data-stu-id="1fa49-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="1fa49-130">編碼錯誤通常會顯示為指令碼的剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="1fa49-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="1fa49-131">如果您發現指令碼中有奇怪的字元序列，這可能就是問題。</span><span class="sxs-lookup"><span data-stu-id="1fa49-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="1fa49-132">在下列範例中，短破折號 (`–`) 顯示為字元 `â€“`：</span><span class="sxs-lookup"><span data-stu-id="1fa49-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="1fa49-133">此問題發生的原因是 VSCode `–`以 UTF-8為位元組`0xE2 0x80 0x93`編碼字元。</span><span class="sxs-lookup"><span data-stu-id="1fa49-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="1fa49-134">當這些位元組解碼為 Windows-1252 時，它們就會解譯為字元 `â€“`。</span><span class="sxs-lookup"><span data-stu-id="1fa49-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="1fa49-135">您可能看到的一些奇怪字元序列包括：</span><span class="sxs-lookup"><span data-stu-id="1fa49-135">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="1fa49-136">`â€“`，而非 `–`</span><span class="sxs-lookup"><span data-stu-id="1fa49-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="1fa49-137">`â€”`，而非`—`</span><span class="sxs-lookup"><span data-stu-id="1fa49-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="1fa49-138">`Ã„2`，而非`Ä`</span><span class="sxs-lookup"><span data-stu-id="1fa49-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="1fa49-139">`Â`，而非 ` ` (不分行空格)</span><span class="sxs-lookup"><span data-stu-id="1fa49-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="1fa49-140">`Ã©`，而非`é`</span><span class="sxs-lookup"><span data-stu-id="1fa49-140">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="1fa49-141">這份方便的[參考](https://www.i18nqa.com/debug/utf8-debug.html)列出指出 UTF-8/Windows-1252 編碼問題的常見模式。</span><span class="sxs-lookup"><span data-stu-id="1fa49-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="1fa49-142">VSCode 中的 PowerShell 延伸模組如何與編碼互動</span><span class="sxs-lookup"><span data-stu-id="1fa49-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="1fa49-143">PowerShell 延伸模組與指令碼互動的幾種方式：</span><span class="sxs-lookup"><span data-stu-id="1fa49-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="1fa49-144">使用 VSCode 編輯指令碼時，VSCode 就會將內容傳送至延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1fa49-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="1fa49-145">[語言伺服器通訊協定][]規定使用 UTF-8 傳送此內容。</span><span class="sxs-lookup"><span data-stu-id="1fa49-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="1fa49-146">因此，延伸模組不可能取得錯誤的編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="1fa49-147">當指令碼直接在整合式主控台中執行時，PowerShell 會直接從檔案讀取它們。</span><span class="sxs-lookup"><span data-stu-id="1fa49-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="1fa49-148">如果 PowerShell 編碼和 VSCode 編碼不同，這裡就會出錯。</span><span class="sxs-lookup"><span data-stu-id="1fa49-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="1fa49-149">當使用 VSCode 開啟之指令碼參考另一個非以 VSCode 開啟的指令碼時，延伸模組會回復成從檔案系統載入該指令碼內容。</span><span class="sxs-lookup"><span data-stu-id="1fa49-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="1fa49-150">PowerShell 延伸模組預設為 UTF-8 編碼，但會使用[位元組順序標記][] (或稱 BOM) 偵測選取正確的編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="1fa49-151">假設編碼無 BOM 格式時，就會發生問題 (例如 [UTF-8][] 不使用 BOM 和 [Windows-1252][])。</span><span class="sxs-lookup"><span data-stu-id="1fa49-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="1fa49-152">PowerShell 延伸模組預設使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1fa49-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="1fa49-153">延伸模組不能變更 VSCode 的編碼設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="1fa49-154">如需詳細資訊，請參閱[問題 #824](https://github.com/Microsoft/vscode/issues/824)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="1fa49-155">選擇正確的編碼</span><span class="sxs-lookup"><span data-stu-id="1fa49-155">Choosing the right encoding</span></span>

<span data-ttu-id="1fa49-156">不同的系統和應用程式可以使用不同編碼：</span><span class="sxs-lookup"><span data-stu-id="1fa49-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="1fa49-157">在 .NET Standard (網路) 和 Linux 環境中，UTF-8 目前是主流編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="1fa49-158">許多 .NET Framework 應用程式使用 [UTF-16][]。</span><span class="sxs-lookup"><span data-stu-id="1fa49-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="1fa49-159">基於歷史原因，這有時稱為 "Unicode"，這個詞彙現在意指包含 UTF-8 和 UTF-16 的廣義[標準](https://en.wikipedia.org/wiki/Unicode)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="1fa49-160">在 Windows 中，許多比 Unicode 更早的原生應用程式，根據預設仍繼續使用 Windows-1252。</span><span class="sxs-lookup"><span data-stu-id="1fa49-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="1fa49-161">Unicode 編碼方式也有位元組順序標記 (BOM) 的概念。</span><span class="sxs-lookup"><span data-stu-id="1fa49-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="1fa49-162">BOM 發生在文字的開頭，告訴解碼器該文字使用哪種編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="1fa49-163">針對多位元組編碼，BOM 也會指出編碼的[字節順序](https://en.wikipedia.org/wiki/Endianness)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="1fa49-164">BOM 設計為很少出現在非 Unicode 文字中的位元組，在有 BOM 時，讓人合理猜測文字是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="1fa49-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="1fa49-165">BOM 為選擇性，且使用情況不像在 Linux 環境中那麼熱門，因為各處普遍使用可靠的 UTF-8 慣例。</span><span class="sxs-lookup"><span data-stu-id="1fa49-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="1fa49-166">大部分的 Linux 應用程式假設文字輸入使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="1fa49-167">雖然許多 Linux 應用程式會辨識並正確處理 BOM，但也有很多不能，以致要使用這些應用程式操作文字中的成品。</span><span class="sxs-lookup"><span data-stu-id="1fa49-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="1fa49-168">**因此**：</span><span class="sxs-lookup"><span data-stu-id="1fa49-168">**Therefore**:</span></span>

- <span data-ttu-id="1fa49-169">如果您主要使用 Windows 應用程式和 Windows PowerShell，您應該會比較偏好使用 BOM 的 UTF-8 或 UTF-16 這類編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="1fa49-170">如果您跨平台工作，您應該會偏好使用 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1fa49-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="1fa49-171">如果您主要是在與 Linux 相關聯的環境中工作，您應該會偏好不使用 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1fa49-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="1fa49-172">Windows-1252 和拉丁文-1 基本是舊版的編碼，如果可能，應該避免。</span><span class="sxs-lookup"><span data-stu-id="1fa49-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="1fa49-173">不過，有些較舊的 Windows 應用程式可能依賴它們。</span><span class="sxs-lookup"><span data-stu-id="1fa49-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="1fa49-174">另外值得一提的是，指令碼簽署為[編碼相依](https://github.com/PowerShell/PowerShell/issues/3466)，這表示變更已簽署指令碼的編碼將需要重新簽署。</span><span class="sxs-lookup"><span data-stu-id="1fa49-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="1fa49-175">設定 VSCode</span><span class="sxs-lookup"><span data-stu-id="1fa49-175">Configuring VSCode</span></span>

<span data-ttu-id="1fa49-176">VSCode 的預設編碼為不使用 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1fa49-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="1fa49-177">若要設定 [VSCode 的編碼][]，請移至 VSCode 設定 (<kbd>Ctrl</kbd>+<kbd>、</kbd>)，並設定 `"files.encoding"` 設定：</span><span class="sxs-lookup"><span data-stu-id="1fa49-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="1fa49-178">可能的值為：</span><span class="sxs-lookup"><span data-stu-id="1fa49-178">Some possible values are:</span></span>

- <span data-ttu-id="1fa49-179">`utf8`:[UTF-8] 不使用 BOM</span><span class="sxs-lookup"><span data-stu-id="1fa49-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="1fa49-180">`utf8bom`:[UTF-8] 使用 BOM</span><span class="sxs-lookup"><span data-stu-id="1fa49-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="1fa49-181">`utf16le`:位元組由小到大的 [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="1fa49-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="1fa49-182">`utf16be`:位元組由大到小的 [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="1fa49-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="1fa49-183">`windows1252`:[Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="1fa49-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="1fa49-184">您應該會在 GUI 檢視中取得它的下拉式清單，或在 JSON 檢視中自動完成它。</span><span class="sxs-lookup"><span data-stu-id="1fa49-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="1fa49-185">您也可以在有可能時，將下列項目新增至自動偵測編碼：</span><span class="sxs-lookup"><span data-stu-id="1fa49-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="1fa49-186">如果您不希望這些設定影響所有的檔案類型，VSCode 也允許依照語言的設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="1fa49-187">將設定放入 `[<language-name>]` 欄位，建立語言特定設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="1fa49-188">例如：</span><span class="sxs-lookup"><span data-stu-id="1fa49-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="1fa49-189">設定 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fa49-189">Configuring PowerShell</span></span>

<span data-ttu-id="1fa49-190">PowerShell 的預設編碼隨版本而異：</span><span class="sxs-lookup"><span data-stu-id="1fa49-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="1fa49-191">在 PowerShell 6+ 中，所有平台的預設編碼都是不使用 BOM 的 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="1fa49-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="1fa49-192">在 Windows PowerShell 中，預設編碼通常是 Windows-1252，即[拉丁文-1][] 的延伸模組，也稱為 ISO 8859-1。</span><span class="sxs-lookup"><span data-stu-id="1fa49-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="1fa49-193">在 PowerShell 5+ 中，您可以使用下列內容找到您的預設編碼：</span><span class="sxs-lookup"><span data-stu-id="1fa49-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="1fa49-194">下列[指令碼](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)可用來判斷 PowerShell 工作階段會針對不使用 BOM 的指令碼推斷何種編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="1fa49-195">您可以使用設定檔設定，設定 PowerShell 更廣泛使用指定的編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="1fa49-196">查看下列文章：</span><span class="sxs-lookup"><span data-stu-id="1fa49-196">See the following articles:</span></span>

- <span data-ttu-id="1fa49-197">StackOverflow 上有關 PowerShell 編碼之 [@mklement0] 的[解答](https://stackoverflow.com/a/40098904)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="1fa49-198">在 PowerShell 中處理無 BOM UTF-8 輸入之 [@rkeithhill] [ 的部落格文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="1fa49-199">您無法強制 PowerShell 使用特定的輸入編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="1fa49-200">沒有 BOM 時，PowerShell 5.1 和較舊版本預設使用 Windows-1252 編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="1fa49-201">基於互通性考量，最好使用 BOM 以 Unicode 格式儲存指令碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1fa49-202">您能接觸到 PowerShell 指令碼的任何其他工具，都可能會受到您的編碼選擇影響，或將您的指令碼重新編碼成其他編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="1fa49-203">現有的指令碼</span><span class="sxs-lookup"><span data-stu-id="1fa49-203">Existing scripts</span></span>

<span data-ttu-id="1fa49-204">檔案系統中現有指令碼可能需要重新編碼成您新選擇的編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="1fa49-205">在 VSCode 的下方列中，您會看到 UTF-8 標籤。</span><span class="sxs-lookup"><span data-stu-id="1fa49-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="1fa49-206">按一下它開啟動作列，然後選取 **以編碼方式儲存**。</span><span class="sxs-lookup"><span data-stu-id="1fa49-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="1fa49-207">您現在可為該檔案選擇新的編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="1fa49-208">如需完整指示，請參閱 [VSCode 的編碼][]。</span><span class="sxs-lookup"><span data-stu-id="1fa49-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="1fa49-209">如果您需要重新編碼多個檔案，您可以使用下列指令碼：</span><span class="sxs-lookup"><span data-stu-id="1fa49-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="1fa49-210">PowerShell 整合式指令碼環境 (ISE)</span><span class="sxs-lookup"><span data-stu-id="1fa49-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="1fa49-211">如果您也使用 PowerShell ISE 來編輯指令碼，您需要同步該處的編碼設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="1fa49-212">ISE 應該會接受 BOM，但它也可能使用反映來[設定編碼](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="1fa49-213">請注意，這不會在啟動之間保存。</span><span class="sxs-lookup"><span data-stu-id="1fa49-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="1fa49-214">原始檔控制軟體</span><span class="sxs-lookup"><span data-stu-id="1fa49-214">Source control software</span></span>

<span data-ttu-id="1fa49-215">有些原始檔控制工具，例如 GIT，會忽略編碼；GIT 只追蹤位元組。</span><span class="sxs-lookup"><span data-stu-id="1fa49-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="1fa49-216">其他工具，例如 Azure DevOps 或 Mercurial，則不然。</span><span class="sxs-lookup"><span data-stu-id="1fa49-216">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="1fa49-217">有些以 GIT 為基礎的工具甚至依賴解碼文字。</span><span class="sxs-lookup"><span data-stu-id="1fa49-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="1fa49-218">發生這種情況時，請務必：</span><span class="sxs-lookup"><span data-stu-id="1fa49-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="1fa49-219">在原始檔控制中設定文字編碼，以符合您的 VSCode 設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="1fa49-220">確定所有檔案皆已使用相關的編碼簽入原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="1fa49-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="1fa49-221">請小心透過原始檔控制所收到的編碼變更。</span><span class="sxs-lookup"><span data-stu-id="1fa49-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="1fa49-222">此項目的鑰匙符號指出有變更差異，卻又似乎沒有任何變更 (因為位元組變更，但字元未變更)。</span><span class="sxs-lookup"><span data-stu-id="1fa49-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="1fa49-223">共同作業者的環境</span><span class="sxs-lookup"><span data-stu-id="1fa49-223">Collaborators' environments</span></span>

<span data-ttu-id="1fa49-224">在設定原始檔控制的最上層，確定您共用之任何檔案的共同作業者沒有設定，無法透過重新編碼 PowerShell 檔案來覆寫您的編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="1fa49-225">其他程式</span><span class="sxs-lookup"><span data-stu-id="1fa49-225">Other programs</span></span>

<span data-ttu-id="1fa49-226">可讀取或寫入 PowerShell 指令碼的任何其他程式都能夠對它重新編碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="1fa49-227">以下列出一些範例：</span><span class="sxs-lookup"><span data-stu-id="1fa49-227">Some examples are:</span></span>

- <span data-ttu-id="1fa49-228">使用剪貼簿複製並貼上指令碼。</span><span class="sxs-lookup"><span data-stu-id="1fa49-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="1fa49-229">這是常見的案例，例如：</span><span class="sxs-lookup"><span data-stu-id="1fa49-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="1fa49-230">將指令碼複製到 VM</span><span class="sxs-lookup"><span data-stu-id="1fa49-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="1fa49-231">複製電子郵件或網頁的指令碼</span><span class="sxs-lookup"><span data-stu-id="1fa49-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="1fa49-232">Microsoft Word 或 PowerPoint 文件為指令碼的複製來源或目標</span><span class="sxs-lookup"><span data-stu-id="1fa49-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="1fa49-233">其他文字編輯器，例如：</span><span class="sxs-lookup"><span data-stu-id="1fa49-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="1fa49-234">[記事本]</span><span class="sxs-lookup"><span data-stu-id="1fa49-234">Notepad</span></span>
  - <span data-ttu-id="1fa49-235">vim</span><span class="sxs-lookup"><span data-stu-id="1fa49-235">vim</span></span>
  - <span data-ttu-id="1fa49-236">任何其他 PowerShell 指令碼編輯器</span><span class="sxs-lookup"><span data-stu-id="1fa49-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="1fa49-237">文字編輯公用程式，例如：</span><span class="sxs-lookup"><span data-stu-id="1fa49-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="1fa49-238">PowerShell 重新導向運算子，例如 `>` 和 `>>`</span><span class="sxs-lookup"><span data-stu-id="1fa49-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="1fa49-239">檔案傳輸程式，例如：</span><span class="sxs-lookup"><span data-stu-id="1fa49-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="1fa49-240">網頁瀏覽器，下載指令碼時</span><span class="sxs-lookup"><span data-stu-id="1fa49-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="1fa49-241">檔案共用</span><span class="sxs-lookup"><span data-stu-id="1fa49-241">A file share</span></span>

<span data-ttu-id="1fa49-242">這些工具有些會處理位元組而不處理文字，有些則提供編碼設定。</span><span class="sxs-lookup"><span data-stu-id="1fa49-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="1fa49-243">在您需要設定編碼的這些情況下，您需要讓它和您的編輯器編碼一樣，以免發生問題。</span><span class="sxs-lookup"><span data-stu-id="1fa49-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="1fa49-244">在 PowerShell 中編碼的其他資源</span><span class="sxs-lookup"><span data-stu-id="1fa49-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="1fa49-245">有幾篇關於編碼和 PowerShell 設定編碼的文章值得閱讀：</span><span class="sxs-lookup"><span data-stu-id="1fa49-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="1fa49-246">[StackOverflow 上有關 PowerShell 編碼之 [@mklement0] 的摘要 ](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="1fa49-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="1fa49-247">之前提出有關 vscode-PowerShell 的編碼問題：</span><span class="sxs-lookup"><span data-stu-id="1fa49-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="1fa49-248">#1308</span><span class="sxs-lookup"><span data-stu-id="1fa49-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="1fa49-249">#1628</span><span class="sxs-lookup"><span data-stu-id="1fa49-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="1fa49-250">#1680</span><span class="sxs-lookup"><span data-stu-id="1fa49-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="1fa49-251">#1744</span><span class="sxs-lookup"><span data-stu-id="1fa49-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="1fa49-252">#1751</span><span class="sxs-lookup"><span data-stu-id="1fa49-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="1fa49-253">傳統「約耳談軟體」有關 Unicode 的文章</span><span class="sxs-lookup"><span data-stu-id="1fa49-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="1fa49-254">.NET Standard 中的編碼</span><span class="sxs-lookup"><span data-stu-id="1fa49-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[拉丁文-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[位元組順序標記]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[語言伺服器通訊協定]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode 的編碼]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
